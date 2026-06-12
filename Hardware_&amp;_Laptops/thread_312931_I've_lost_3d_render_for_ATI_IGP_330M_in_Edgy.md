---
title: "I've lost 3d render for ATI IGP 330M in Edgy"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by parrimin on 2006-12-05
Hi,
I just installed a new installation of Edgy, and I had no problem, but i tried to update my drivers to newers, and x-server crashed ](*,) 

I tried to install fglrx, and others, but now, the only drivers that runs are vesa, and does´t run so much cool.

Knowing that when i first installed the SO there was no problem, im just asking how can i go back to that state of my video drivers. I can´t remember what drivers where installed then. If somebody running this video card without problems can respons with his xorg.conf file, it will be enough i think.
And the last, im uninstalling and installing the drivers in the correct way?The way I install other driver is:
sudo dpkg-reconfigure xserver-xorg, and try other driver, like, ati, or fglrx.

Sorry for my english. I know if I install from zero another time it will run, but i'have installed several times, and i can´t do it forever. I´d like to know what´s happening in my PC! Thanks

---

### Post by pay on 2006-12-05
I know that Ati dropped support for alot of cards so you might need to try an older driver like 8.26.18

---

### Post by parrimin on 2006-12-05
Can you explain me how to install that driver?

---

### Post by pay on 2006-12-05
Try method 2 from this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) but instead of downloading the 8.31.5 driver, downlaod the 8.26.18 driver from here [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run) btw the driver that was in the dapper repositories was the 8.25.18 driver so you might want to try that one (seeing that you have said that it has worked for you before) from here [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run)

---

### Post by parrimin on 2006-12-05
Thanks a lot for your help, but im installing from zero another time. I´ll explain what i tried:
1. First i boot form live cd to copy the xorg.conf file, mounte the partition where is my ubuntu installation and copied the file. I rebooted, but the x-server has not started. I tiped startx, but i the direct render is not running. Otherwise, i couldn´t search any tutorial saying how to configure to start x automatically.
2. I tried to re-install drivers looking at the tutorials you say (they were the tutorials that crashed the initial setup), but now, i cant connect to the repositories. 

I was 3 days trying to repair this, but i have to give up, i want a laptop running, and its faster to install another time from zero.
Thanks for your help, but you know what happened? What should i do if i cant start xserver automatically another time? And most important, how can i backup the initial configuration to have the possibility to turn back if i crash the installation another time? Im sure i will!:-|

---

### Post by pay on 2006-12-05
To backup the xorg.conf file type```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```and to revert back type```
sudo cp -r /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```The problem sounds like a bug with ati opensource drivers and xorg 7.1 as I had the same problem with a different ati card when I updated xorg 7 to 7.1. If the problem happens again try booting a liveCD and chrooting into your installation to fix the problem. To chroot into the environment try ```
sudo su
mkdir /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
env-update
source /etc/profile
export PS1="(chroot) $PS1"
```Hopefully you don't have to do what I did and it works for you this time. Good luck.

---

### Post by parrimin on 2006-12-05
Thanks Pay. I thing from now on, i will come to this forum. I was in spanish forums, and there were no answers, and all i tried i found googling. 
Thank you another time for your help:)

---

### Post by parrimin on 2006-12-05
Aps, the las question, what´s the meaning os chrooting, and why are you mounting hda3?

---

### Post by pay on 2006-12-05
If you chroot you can use your installation on your harddisk but with a liveCD environment. Useful for fixing problems when you can't boot your kernel or your drivers aren't working etc. That above chroot guide is brief and is only an example. Mount your / partition which on my system is hda3 but on yours it may be ha2 or hc2 etc.

---

