---
title: "Splash screen disappears"
date: 2008-07-18
forum: General Help
---

### Post by feistybill on 2008-07-18
I installed Ubuntu 8.04.1 on 2 different computers (a notebook and a desktop pc). I used ReiserFS for both installations.

On one of them (the notebook) when Ubuntu is loading and the progress bar is about 1/4 full, the splash screen disappears and I can see the text messages scrolling (the last text line is "Filesystem is clean"), just like when you remove the QUIET and SPLASH options from Grub's menu.lst.

Then it continues loading until the Gnome login finally appears.

Any suggestions on how I can fix this?

---

### Post by joshsmith on 2008-07-18
easy solution, use ext3

anyway, im guessing it is scannign the hard drive
if you edit the file /etc/fstab you can control if a specific partition gets scanned, by changing the number in the <pass> column to zero

---

### Post by feistybill on 2008-07-18
ext3 ? ugh... no, thanks.

Anyway, looks like it's one of these 2 bugs:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658)

I'm going to try the solutions that have been posted there.


EDIT: Nope, didn't work... editing /etc/init.d/checkfs.sh doesn't seem to help either, so I just renamed fsck and now everything works (except I have to start fsck manually each now and then).

---

