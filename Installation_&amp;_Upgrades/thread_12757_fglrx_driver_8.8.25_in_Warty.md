---
title: "fglrx driver 8.8.25 in Warty"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by dandeguire on 2005-01-26
I just got a new Dell Dimension 4700 with an ATI Radeon X300 card.  I carved out a partion on my hard drive and installed Warty.  XFree86 fails to recognize my video card.  I've downloaded the 8.8.25 driver from ATI and converted it to .deb, but I can't get it to install.

Following the advice from another thread, I tried the following:
sudo dpkg -i --force-all fglrx*.deb     (this worked just fine)
cd /lib/modules/fglrx/build_mod        (this worked too)
sudo sh make.sh           (crash and burn)

make produced a file called make.log with the following:
[INDENT]ATI module generator V 2.0
==========================
initializing...
build_date =Wed Jan 26 18:40:25 UTC 2005
uname -a =Linux ubuntu 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.8.1-3-386
uname -v =#1 Tue Oct 12 12:41:57 BST 2004
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x   34 root     root         4096 2005-01-26 18:39 /usr/include
.
total 8
drwxr-xr-x    2 root     root         4096 2005-01-26 18:39 ATI
drwxr-xr-x    7 root     root         4096 2005-01-26 01:35 rpm
.
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h[/INDENT]
What do i need to install to get that directory?
Has anyone got this driver working with Warty and a Radeon X300?

I've been working on this for 4 days now, and my wife is beginning to consider me a stranger.

Thanks for your help!
Dan

---

### Post by jensyt on 2005-01-26
Your problem is that your source version (/usr/src/linux) doesn't match the current kernel you're running. One cheap way to change this is to manually edit the file listed to whatever version kernel you're running. Though I don't suggest it, and don't know how to really fix it otherwise, there must be a simpler way to do it.

EDIT: Try changing that file to reflect what the "uname -r" command states.

---

### Post by mirtux on 2005-02-11
Hi,
   you can have a look here [http://www.ubuntuforums.org/showthread.php?t=13226](http://www.ubuntuforums.org/showthread.php?t=13226). Hope this can help,
 
 MC

---

