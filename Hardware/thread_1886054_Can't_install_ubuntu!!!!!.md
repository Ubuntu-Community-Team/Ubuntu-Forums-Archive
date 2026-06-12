---
title: "Can't install ubuntu!!!!!"
date: 2011-11-24
forum: Hardware
---

### Post by xXDestroyerGRXx on 2011-11-24
Hello i have this bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/864155](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/864155)

Please help me!!!!!!!!!!!!!

---

### Post by collisionystm on 2011-11-24
> **xXDestroyerGRXx said:**
> Hello i have this bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/864155](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/864155)

Please help me!!!!!!!!!!!!!


Reboot your computer with the Live-CD. Keep tapping up arrow key. At the menu, choose your language. Press F6 choose NOMODESET. Hit esc key. Choose Live mode

You will be at a text login. If not, hit CTRL + ALT + F2

type 
sudo bash

apt-get remove xserver-xorg-video-radeon

lightdm restart

You should now have a GUI.

Install.

When system reboots. Do the same thing. Except you will be at a grub install instead of language selection. Hit the letter 'e' on your keyboard. Go down by where it says 'splash'. right before it, type nomodeset

do same steps as before with removing xserver-xorg-video-radeon

once up, load firefox. Download catalyst driver

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

once downloaded, right click on file, go to permissions, make executable

run the install, choose 'Express Install'

When finished open a terminal

type

sudo bash

aticonfig --initial -f


Reboot.

Your good to go.

---

### Post by xXDestroyerGRXx on 2011-11-24
i can't do anything because i can't see anything dude

---

### Post by collisionystm on 2011-11-24
> **xXDestroyerGRXx said:**
> i can't do anything because i can't see anything dude


I realize that. I had the same problem. Follow my steps. You need to interrupt the boot process before the screen goes black.

---

