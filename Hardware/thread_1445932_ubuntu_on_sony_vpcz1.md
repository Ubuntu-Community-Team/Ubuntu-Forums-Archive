---
title: "ubuntu on sony vpcz1"
date: 2010-04-03
forum: Hardware
---

### Post by space9999 on 2010-04-03
just got a z series sony vaio laptop vpcz11c5e (hdd, i7, 8gb) and cannot get ubuntu 64 to work.

on install the wireless, video resolution and mouse do not work - -

the sony has a nvidia graphics card that ubuntu does not recognis, and gives an 800x600 resolution that i cannot get to change, if i install the invidia-glx-185, ubuntu black screens and does nothing.

i managed to get the wireless to work with
dmesg | grep iwl
rfkill list
sudo apt-get install linux-backports-modules-karmic-generic
sudo rmmod -f iwlagn
sudo modprobe iwlagn

i have not tried to debug the mouse as yet.

thanks for any help

space

---

### Post by aleixsr on 2010-05-01
> **space9999 said:**
> just got a z series sony vaio laptop vpcz11c5e (hdd, i7, 8gb) and cannot get ubuntu 64 to work.

on install the wireless, video resolution and mouse do not work - -

the sony has a nvidia graphics card that ubuntu does not recognis, and gives an 800x600 resolution that i cannot get to change, if i install the invidia-glx-185, ubuntu black screens and does nothing.

i managed to get the wireless to work with
dmesg | grep iwl
rfkill list
sudo apt-get install linux-backports-modules-karmic-generic
sudo rmmod -f iwlagn
sudo modprobe iwlagn

i have not tried to debug the mouse as yet.

thanks for any help

space

Same problem here, any way to boot X correctly?

---

### Post by Gwaelk on 2010-05-05
Hi,
I do... but was a bit strange procedure. First of all, it is only working with karmic and lower. I have tried on lucid lynx but no way since I do not have any virtual console to go in text mode even in the Rescue Mode where it is supposed to be the case. So, on lucid lynx, only get a blank screen even if I did not installed X11 !!! Strange isn't it ?

So, how to proceed:
0- Download the last nvidia driver from the nvidia site. At the time of writing it is called: NVIDIA-Linux-x86_64-195.36.24-pkg2.run
1- Boot in rescue mode (options ro and single)
2- Be sure that neither gdm not x11 is working (ps aux | grep xxx)
3- launch the Nvidia install in text mode:
sudo ./NVIDIA-Linux-x86_64-195.36.24-pkg2.run
(chmod 755 before if needed)
4- At the end of the install, choose to generate an xorg config file
5- startx

If X11 is now working in 1600x900 then it is ok, just reboot...

By the way, you should modify /etc/default/grub to add "i8042.nopnp" in the linux boot options and you need to make a: grub-install as root to modify grub.
Then X11 is working AND the touchpad is working

I hope this help...

---

