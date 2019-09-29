# git -- git において config ファイルの lock に失敗する場合の挙動を変更する為の修正版

## 概要

分散型バージョン管理システムである [git][GIT_] において、 VFAT ファイルシステム及び [Android OS][ANDR] 及び [Debian noroot 環境][DBNR]における外部ストレージ領域において、 ```git clone``` コマンド等を用いて新しい git リポジトリを作成する場合に、 ```.git/config``` ファイルの lock ファイルについて lock ファイルの権限の変更に失敗するために、 ```.git/config``` の lock に失敗し、リポジトリが作成できない問題が発生しています。

この git リポジトリに置かれている [git][GIT_] のソースコードは、 [git][GIT_] において、前述のような ```.git/config``` ファイルの lock に失敗する場合の挙動について、 lock の失敗を無視するかどうかの [git][GIT_] の挙動を設定する事を可能にするように修正したものです。

また、 [git][GIT_] のインストール時において、[ハードリンク][LINK]に代えて[シンボリックリンク][SLNK]を使用する修正も同時に加えています。

なお、この git リポジトリに置かれている [git][GIT_] のソースコードは、 [git][GIT_] リポジトリ "[git 2.17.0 以降において config ファイルの lock に失敗する場合の挙動を変更する差分ファイル][GITC]" に置かれた差分ファイルの作成用のリポジトリです。

実際に lock の失敗を無視するかどうかの [git][GIT_] の挙動を設定する事を可能にする git をビルドする際には、前述のリポジトリを参照して、オリジナルの git のソースコードに差分ファイルを適用してビルドするようにして下さい。

## 使用条件

この git リポジトリに置かれている [git][GIT_] のソースコードは、 [Junio C Hamano 氏][JUNI]を始めとする git の開発コミュニティ によるコードを、 [Z.OOL. (mailto:zool@zool.jpn.org)][ZOOL] によって、git において config ファイルの lock に失敗する場合の挙動を変更するように修正したものです。

従って、本ソースコードは、 git のライセンスと同様である [Lesser GPL 2.1][LGPL] に基づいて配布されるものとします。詳細については、本リポジトリに同梱する ```LGPL-2.1``` を参照して下さい。

## 追記

以下に、オリジナルの [git][GIT_] のソースコードの [README.md][READ] の原文を示します。

----

[![Build Status](https://dev.azure.com/git/git/_apis/build/status/git.git)](https://dev.azure.com/git/git/_build/latest?definitionId=11)

Git - fast, scalable, distributed revision control system
=========================================================

Git is a fast, scalable, distributed revision control system with an
unusually rich command set that provides both high-level operations
and full access to internals.

Git is an Open Source project covered by the GNU General Public
License version 2 (some parts of it are under different licenses,
compatible with the GPLv2). It was originally written by Linus
Torvalds with help of a group of hackers around the net.

Please read the file [INSTALL][] for installation instructions.

Many Git online resources are accessible from <https://git-scm.com/>
including full documentation and Git related tools.

See [Documentation/gittutorial.txt][] to get started, then see
[Documentation/giteveryday.txt][] for a useful minimum set of commands, and
`Documentation/git-<commandname>.txt` for documentation of each command.
If git has been correctly installed, then the tutorial can also be
read with `man gittutorial` or `git help tutorial`, and the
documentation of each command with `man git-<commandname>` or `git help
<commandname>`.

CVS users may also want to read [Documentation/gitcvs-migration.txt][]
(`man gitcvs-migration` or `git help cvs-migration` if git is
installed).

The user discussion and development of Git take place on the Git
mailing list -- everyone is welcome to post bug reports, feature
requests, comments and patches to git@vger.kernel.org (read
[Documentation/SubmittingPatches][] for instructions on patch submission).
To subscribe to the list, send an email with just "subscribe git" in
the body to majordomo@vger.kernel.org. The mailing list archives are
available at <https://public-inbox.org/git/>,
<http://marc.info/?l=git> and other archival sites.

Issues which are security relevant should be disclosed privately to
the Git Security mailing list <git-security@googlegroups.com>.

The maintainer frequently sends the "What's cooking" reports that
list the current status of various development topics to the mailing
list.  The discussion following them give a good reference for
project status, development direction and remaining tasks.

The name "git" was given by Linus Torvalds when he wrote the very
first version. He described the tool as "the stupid content tracker"
and the name as (depending on your mood):

 - random three-letter combination that is pronounceable, and not
   actually used by any common UNIX command.  The fact that it is a
   mispronunciation of "get" may or may not be relevant.
 - stupid. contemptible and despicable. simple. Take your pick from the
   dictionary of slang.
 - "global information tracker": you're in a good mood, and it actually
   works for you. Angels sing, and a light suddenly fills the room.
 - "goddamn idiotic truckload of sh*t": when it breaks

[INSTALL]: INSTALL
[Documentation/gittutorial.txt]: Documentation/gittutorial.txt
[Documentation/giteveryday.txt]: Documentation/giteveryday.txt
[Documentation/gitcvs-migration.txt]: Documentation/gitcvs-migration.txt
[Documentation/SubmittingPatches]: Documentation/SubmittingPatches

<!-- 外部リンク一覧 -->

[DBNR]:https://play.google.com/store/apps/details?id=com.cuntubuntu&hl=ja
[ANDR]:https://www.android.com/intl/ja_jp/
[GIT_]:https://git-scm.com/
[GTGH]:https://github.com/git/git
[LINK]:http://man7.org/linux/man-pages/man2/link.2.html
[SLNK]:http://man7.org/linux/man-pages/man2/symlink.2.html
[TERM]:https://termux.com/
[GITC]:https://github.com/z80oolong/git-config-fix
[JUNI]:mailto:gitster@pobox.com
[TAP1]:https://github.com/z80oolong/homebrew-git
[ZOOL]:http://zool.jpn.org/
[LGPL]:http://www.gnu.org/licenses/lgpl-2.1.html
[READ]:https://github.com/git/git/blob/master/README.md
