---
title: "Compiling kernel before having internet access"
date: 2005-11-03
forum: General Help
---

### Post by octomancer on 2005-11-03
Hi all,

A friend of mine has just installed 5.10 Breezy from CD. His internet connection is via a Zyxel 630-C1 modem, which is not supported in the stock kernel. I have installed Ubuntu myself so I can do the same things as him and make it easier for me to help him. Although my friend is a noob, I've been using Linux for 7 years and Linux sysadmin is part of my job. All my experience is with RedHack and Gentoo though. Tried Debian for a bit at home, it did not float my boat. During all this, I have internet access, he doesn't. If he needs anything he has to reboot into Windows to get it.

I have found the driver for him from [http://accessrunner.sourceforge.net](http://accessrunner.sourceforge.net) and this requires a kernel recompile. This is where the problems start.

We're using Synaptic to install things. We've added the install CD as a source of packages via 'Edit->Add CD-ROM ...'.

Trying to find the kernel sources on the install CD proved fruitless. We downloaded a stock 2.6.14 kernel from kernel.org, it's now untarred in /usr/src with the linux symlinx created. However "make menuconfig" replies with

root@ubuntu:/usr/src/linux# make menuconfig
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

Synaptic tells me that all packages with a name matching '.*curses.*' are installed. Yet 'updatedb; locate curses.h' produces no output.

"make xconfig" fails too:

root@ubuntu:/usr/src/linux# make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Error 1
make: *** [xconfig] Error 2

"locate libqt" is not particularly helpful:

root@ubuntu:/usr/src/linux# locate libqt
/var/lib/dpkg/info/libqthreads-12.shlibs
/var/lib/dpkg/info/libqthreads-12.list
/var/lib/dpkg/info/libqthreads-12.postinst
/var/lib/dpkg/info/libqthreads-12.postrm
/var/lib/dpkg/info/libqthreads-12.md5sums
/usr/share/doc/libqthreads-12
/usr/share/doc/libqthreads-12/changelog.Debian.gz
/usr/share/doc/libqthreads-12/copyright
/usr/lib/libqthreads.so.12.3.0
/usr/lib/libqthreads.so.12

( Incidentally, I'm aware that root doesn't by default get access to the X11 display, however these commands fail as an ordinary user too. )

QT is not installable from Synaptic for us.

So this is where we are ... ](*,)

Somebody please tell me we're not left with "make config". Please!

If anyone can think of an alternative way we can make this happen, it would be hugely appreciated. What I'm about to try is this:

Reboot into Gentoo and "make xconfig" for my stock 2.6.14 kernel. Enable what I think should make a bootable kernel for him and send him my .config file, tweaked to compile the Zyxel driver code (he already has the source for it). Then get him to compile, install and boot the new kernel.

TIA
Rich

---

### Post by mlomker on 2005-11-03
You'll need **libncurses5-dev** and **kernel-package** if you want to build a kernel the [debian way.]("http://www.projektfarm.com/en/support/howto/debian_kernel_compile.html")

I should think those are on the CD, otherwise you could grab the packages from packages.ubuntu.com from another box.

---

