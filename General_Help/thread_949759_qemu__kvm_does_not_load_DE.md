---
title: "qemu / kvm does not load DE"
date: 2008-10-16
forum: General Help
---

### Post by bobotoes on 2008-10-16
Attempts to start a linux installation cd (e.g. ubuntu 8.04-1) with the following:
```
$ kvm -boot d -cdrom ubuntu-8.04.1-desktop-i386.iso -hda qemu_ubuntu_i386.img
```
do not work. In this case, everything appears to start fine until the graphical environment. The Hardy Heron Wallpaper appears and a mouse, but no more. The mouse never freezes but nothing else appears.
Similarly, the same problem happens with Fedora 9 livecd.

---

### Post by bodhi.zazen on 2008-10-16
Yes there is an issue with the mouse in that version of Ubuntu (and Fedora).

I suggest you try 8.10 Beta. Or you can try the Fedora Beta.

Te other option is to re-configure the mouse, but this is a bit of a hassle (and even more so to do with every boot).

There are a number of bug reports on this, here are two:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/kvm/+bug/243677](https://bugs.launchpad.net/ubuntu/intrepid/+source/kvm/+bug/243677)

[https://bugs.launchpad.net/ubuntu/intrepid/+source/kvm/+bug/251480](https://bugs.launchpad.net/ubuntu/intrepid/+source/kvm/+bug/251480)

Although these reports are listed in "intrepid" they also affect 8.04.01 (but not 8.04).

---

