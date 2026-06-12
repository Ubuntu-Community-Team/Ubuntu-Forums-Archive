---
title: "Acroread"
date: 2005-11-11
forum: General Help
---

### Post by canadianwriterman on 2005-11-11
Just installed the Acrobat Reader through "Add Applications" successfully. However, the default print command line within Acrobat Reader is:

/usr/bin/lp

This command line does nothing. How do I find out the command line to send something to my installed printer? I print on a BJC8200 though CUPS.

Thanks.

---

### Post by az on 2005-11-11
Try lrp instead of lp.

I think you have to change it every time you use it.  Damn proprietary software!

---

### Post by canadianwriterman on 2005-11-12
Thanks azz, I'll try that.

---

### Post by SickTwist on 2005-11-12
[QUOTE=azz]Try lrp instead of lp.

I think you have to change it every time you use it.  Damn proprietary software![/QUOTE]

Do you mean lpr?

---

### Post by canadianwriterman on 2005-11-12
[QUOTE=azz]Try lrp instead of lp.

I think you have to change it every time you use it.  Damn proprietary software![/QUOTE]

No go. I checked the /usr/bin and there is not "lrp" there (there is an "lp" but Acrobat won't print using it. In fact, I just tried the default PDF reader (Evince) and it sees my printer, but there is no output.

---

### Post by ssam on 2005-11-12
in the inkscape print window changing
```
lp
```
to
```
lp |
```
males it work. (thats the pipe symbol)

it might help here.

any reason for not using evince to read/print pdfs?

edited, got my **p** and **l**s in a muddle

---

### Post by canadianwriterman on 2005-11-12
Also tried the mozilla-acrobat plug-in from Synaptic. Same problem... the default print command is /usr/bib/lp and that doesn't work. There is an option to print from a file, but I'm not sure what file to use or where it's located. Anyone help?

---

### Post by az on 2005-11-12
I have to type in the dark and be very quiet sometimes...  Sorry about the typo - it is lpr.

emma@ubuntu:~$ whereis lpr
lpr: /usr/bin/lpr /usr/bin/X11/lpr /usr/share/man/man1/lpr.1.gz


If lpr is not installed, perhaps this is your problem?  Is the ubuntu-desktop package installed on your system?

lpr is a frontend to cupsys:

emma@ubuntu:~$ apt-cache show cupsys-bsd
Package: cupsys-bsd
Priority: extra
Section: net
Installed-Size: 224
Maintainer: Kenshi Muto <kmuto@debian.org>
Architecture: i386
Source: cupsys
Version: 1.1.23-10ubuntu4
Replaces: lpr, cupsys (<= 1.1.15-2), manpages-fr (<< 0.9.5-1)
Provides: lpr
Depends: libc6 (>= 2.3.4-1), libcupsys2-gnutls10 (>= 1.1.23-1), cupsys-client (=  1.1.23-10ubuntu4), debconf, netbase
Conflicts: lpr, lprng, manpages-fr (<< 0.9.5-1)
Filename: pool/main/c/cupsys/cupsys-bsd_1.1.23-10ubuntu4_i386.deb
Size: 47428
MD5sum: 48561540dabfee42d8b0062b923a58f4
Description: Common UNIX Printing System(tm) - BSD commands
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the BSD commands for interacting with CUPS.  It
 is provides separately to allow CUPS to coexist with other printing
 systems (to a small degree).
 .
 The terms "Common UNIX Printing System" and "CUPS" are trademarks of
 Easy Software Products ([www.easysw.com)](www.easysw.com)), and refer to the original
 source packages from which these packages are made.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-desktop

emma@ubuntu:~$ dpkg -L cupsys-bsd
/.
/usr
/usr/sbin
/usr/sbin/lpc
/usr/bin
/usr/bin/lpq
/usr/bin/lpr
/usr/bin/lprm
/usr/lib
/usr/lib/cups
/usr/lib/cups/daemon
/usr/lib/cups/daemon/cups-lpd
/usr/share
/usr/share/man
/usr/share/man/fr
/usr/share/man/fr/man1
/usr/share/man/fr/man1/lpq.1.gz
/usr/share/man/fr/man1/lpr.1.gz
/usr/share/man/fr/man1/lprm.1.gz
/usr/share/man/fr/man8
/usr/share/man/fr/man8/lpc.8.gz
/usr/share/man/fr/man8/cups-lpd.8.gz
/usr/share/man/man1
/usr/share/man/man1/lpq.1.gz
/usr/share/man/man1/lpr.1.gz
/usr/share/man/man1/lprm.1.gz
/usr/share/man/man8
/usr/share/man/man8/lpc.8.gz
/usr/share/man/man8/cups-lpd.8.gz
/usr/share/man/es
/usr/share/man/es/man1
/usr/share/man/es/man1/lpq.1.gz
/usr/share/man/es/man1/lpr.1.gz
/usr/share/man/es/man1/lprm.1.gz
/usr/share/man/es/man8
/usr/share/man/es/man8/lpc.8.gz
/usr/share/man/es/man8/cups-lpd.8.gz
/usr/share/doc
/usr/share/doc/cupsys-bsd

---

### Post by canadianwriterman on 2005-11-12
Mmmm? Okay, I tried lpr (lpr is in my /usr/bin and I do use the GNOME desktop). Now Abrobal acts like Evince and gpdf when printing: the printer icon flashes on, my printer churns for a moment, the printer icon closes, and there is no output.

---

### Post by ssam on 2005-11-12
can anything print? this sould like a general printing problem

---

