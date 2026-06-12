---
title: "SIS 672, 1280x800, how I got it working, YMMV"
date: 2009-08-21
forum: Hardware
---

### Post by test666 on 2009-08-21
My system:
Fujitsu Esprimo v5515 (SIS 672)
Ubuntu 9.04, fresh install.

The problem:
Only getting 800x600.

The goal:
Getting 1280x800.

I tried for many months to get this working (8.04. 8.10, 9.04), always failing miserably.

I tried other distros (Fedora/Mandriva/Mint)... Not a single one gave me the resolution I wanted.
I returned to Ubuntu (9.04).

0 - I downloaded [xorg-driver-sis671_0.9_i386.deb]("http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb") into my home folder and installed.

On reboot, the system went "crazy", black screen, no errors being reported (AFAIK, too lazy to go through logs in recovery mode+root shell prompt or through the livecd).
I thought that perhaps the system got confused with too many drivers for X under SIS dictatorship.

Time to do some cleaning.
This is the way how it worked for me.

1 - Boot/reboot and choose on the Grub menu "Recovery Mode"
* alternatively, in graphic mode, in the command line, in a terminal window
* type 
* sudo /etc/init.d/gdm stop
* cross fingers
* and X may graciously stop
* OK, so you now jump to step 4

2 - Choose option "Drop to root shell prompt"

3 - Login

4 - Type
sudo su

5 - Type
apt-get remove xserver-video-sis671

5.a - Restart if you think that some goblins are still there (and then go through steps 1-2-3-4-6)

6 - Type 
dpkg -i xorg-driver-sis671_0.9_i386.deb

7 - Reboot (to be on the safe side of things) or exit+startx

As I said before, it worked for me, YMMV.

I tried this procedure in a new fresh install, going directly to step 1 without the install in step 0. It worked. 1280x800 in all its "glory".

---

### Post by _BlondieGirl_ on 2009-09-07
Thank  you so much!!! It finally worked!

---

### Post by test666 on 2009-09-07
Glad to be of service.
You welcome.

---

