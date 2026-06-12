---
title: "Radeon-&gt;fglrx-&gt;Radeon=black screen"
date: 2009-03-11
forum: Hardware
---

### Post by leodp on 2009-03-11
Hi all,

I have an ATI 9600/9700 card (its name is reported confusingly by various lspci versions) working under Ubuntu 8.10

At first it was ok, with open source radeon driver.
Then I installed the proprietary fglrx 9.1beta and 9.2 driver, downloaded from ATI website. I wanted to try if it was better with compiz+Xv video playing. Hot-plug 2-screen config turned out to be a mess.

So I switched back to radeon open source driver.
But I get either a black or a corrupted screen, and I do not have access to the virtual terminals (keyboard freeze?)

On the Xorg log everything seems ok, except maybe for the line:
(II) RADEON(0): DRIScreenInit for fglrx driver
Does this mean the fglrx driver or something related to it is still loaded (not seen on lsmod)?

:( How can I tidy up and have again a working radeon driver? :(



I have tried following the guide in:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and also 
-uninstalling fglrx with the uninstall script in /usr/share/ati
-removing + purging all the fglrx related packages
-reinstalling the radeon/ati related packages
-restoring xorg.conf (with dpgk -phigh ... if I remember correctly now)
and so on, even repeating the sequence in different order.
No way.

Can anybody help me?
Thanks, Leonardo

---

### Post by leodp on 2009-04-08
Hi,
today in 5 minutes I solved the problem. Maybe something was not really necessary, but here is what worked:


1) Remove the manually installed fglrx driver. Install and remove the fglrx packages present in the repositories; removing with --purge should help removing also spare config files
sh /usr/share/ati/fglrx-uninstall.sh
apt-get install xorg-driver-fglrx fglrx-amdcccle
apt-get remove --purge xorg-driver-fglrx fglrx-amdcccle

2) Manually remove other files that may reference to fglrx
rm /etc/X11/xorg.conf
rm -fR  /etc/ati

3) Reinstall xorg related packages and regenerate the config file /etc(X11/xorg.conf
apt-get install --reinstall xserver-xorg-video-vga xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-radeon xserver-common xserver-xorg-core xserver-xorg
dpkg-reconfigure -phigh xserver-xorg


Ciao, Leodp

---

### Post by Nareto on 2009-06-07
oh my god, thank you! what a relief... I built 2.6.30 kernel and X wouldn't start in neither this and the old (2.6.28) kernel... same symptoms as you (black/corrupted screen, nothing unusual in logs)
 
Only difference I am using the Ubuntu-X repositories that contain 6.12.2 version of the radeon driver, and in my repos i didn't have xserver-xorg-video-vga so i didn't reinstall that. Now all is working!

---

### Post by KaitmanFR on 2009-12-22
Thanks you very much Leodp,

My screen was having lot of scrolling problem.
Your solution was just perfect !!

i was experiencing problems with a kernel 2.6.31, ubuntu 9.10, and ati radeon hd 3430.

Solved thanks to you.

P.S : seems like  xserver-xorg-video-vga package does not exist anymore ..

---

