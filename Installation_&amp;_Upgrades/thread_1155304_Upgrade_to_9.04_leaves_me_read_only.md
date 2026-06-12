---
title: "Upgrade to 9.04 leaves me read only"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by ksigler on 2009-05-10
I upgraded to 9.04 yesterday. Upon boot all services come with errors of Read-Only Filesystem.

I have to hit Ctl-Alt-Del to complete the boot process and get dumped to terminal.

I log in and am able to run the following:

sudo mount -o remount,rw /

then

sudo /etc/init.d/gdm restart

and that gets me in just fine. usually. Sometimes it takes one or two reboots for this to work.

Anyone run into this???

I have a a Lenovo Thinkpad T61p with Nvidia. Standard and restricted drivers have the same effect. Things have been running great from 7.x version.

---

### Post by rattking on 2009-05-10
Hi
have you ran fsck on the drives? 
a drive will stay mounted read only if it was not cleanly unmounted

---

### Post by ksigler on 2009-05-10
Thank you! yep. fsck comes up clean. here's where I am:

boot -> Ubuntu splash hangs with status bar

ctl-alt-F1

term shows "loading" 

ctl-alt-del - and rcS then rc5 responds with "term sig" or something

boot process continues with gobs of Read-only failures on services and a Blue Ncurses type screen with GDM failure

ctl-atl-F1 and login works fine

sudo mount -o remount,rw /

then

sudo /etc/init.d/gdm restart

and I'm (usually) in just fine. WTF?

I think all of my problems come down to the HD being mounted on boot as read-only, but /etc/fstab look fine. Even the blkid.

---

