---
title: "installing openoffice 3.x + how do I use Alien?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by saskatchewan on 2009-04-28
eee ubuntu ASUS eee1000

I am trying to install OpenOffice 3.0 and followed two sets of instructions.  Neither have worked.

Here are the instructions and results.

[http://download.openoffice.org/common/instructions.html#linux](http://download.openoffice.org/common/instructions.html#linux)

There are lots of rpm files.  How do I convert them all?

shawn@shawn-laptop:~$ cd OOO300_m15_native_packed-1_en-US.9379
shawn@shawn-laptop:~/OOO300_m15_native_packed-1_en-US.9379$ cd RPMS
shawn@shawn-laptop:~/OOO300_m15_native_packed-1_en-US.9379/RPMS$ rpm -Uvih *rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
shawn@shawn-laptop:~/OOO300_m15_native_packed-1_en-US.9379/RPMS$ alien
You must specify a file to convert.

Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch	    Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version		    Display alien's version number.

shawn@shawn-laptop:~/OOO300_m15_native_packed-1_en-US.9379/RPMS$

---

### Post by benj1 on 2009-04-28
what version are you using, im sure there will be a .deb somewhere.

[here]("http://ubuntuforums.org/showthread.php?t=947924") assuming youre on 8.04 OO 3 was default after that i think

---

