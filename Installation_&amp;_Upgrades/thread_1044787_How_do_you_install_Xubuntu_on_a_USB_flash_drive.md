---
title: "How do you install Xubuntu on a USB flash drive"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by jose158 on 2009-01-19
My brother bought me a mini-ITX computer so that I could set up a home media center. It only came with a 2gb CompactFlash and no optical drives, so I wanted to install Xubuntu via USB flash drive. I installed it with the "Create a USB Starup disk" program but when I put it in the computer, it says:```
Grub: 
``` Why doesn't it work like a live CD?

In case it matters the specs are:

**CPU**: Intel Pentium M 1.80-GHz
**Memory Tota**l: 1GB PC2100 DDR SDRAM
**HD**: 2GB CompactFlash
**Optical Drive**: None
**Network**: Onboard
**Floppy**: None
**Video**: Onboard[B]
Audio[/B]: Onboard
**Ports**: 4 USB, 4 Serial, 1 PCMCIA and 2 ps/2
**Memory**: 1x1GB

Thanks in advance.

---

### Post by empty_tank on 2009-01-19
have you tried unetbootlin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can create a bootable usb if you have the xubuntu iso available

---

### Post by jose158 on 2009-01-19
> **empty_tank said:**
> have you tried unetbootlin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can create a bootable usb if you have the xubuntu iso available
Thanks, I'll try it out and report back

---

### Post by 3DGE on 2009-01-19
> **empty_tank said:**
> have you tried unetbootlin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can create a bootable usb if you have the xubuntu iso available

So with this I don't have to put anything for the install onto my hardrive I can put it all on a flash drive?

---

### Post by jose158 on 2009-01-20
I attempted the unetbootin installation and the USB works, but when trying the alternative install i get the error: ```
Incorrect CD-ROM Detected
The cd-rom drive contains a CD which cannot be used for installation. Please insert a suitable cd to contine with the installation.
```

---

### Post by StopSpazzing on 2009-01-24
If you are trying to install Xubuntu from USB driver link is here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you want to extend the life of your compact-flash AND have it run blazing fast I would recommend doing the following instead:

More information: [http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/](http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/)

I am currently in the process of doing this and transferring it over to my 16gb compact-flash thats in my laptop...I want to see the performance increase but dont want the drive to die on my within >2 years.

Ill let you know how it goes. :)

---

### Post by russu52 on 2009-01-24
hello - there are three things to note:

1. check that your pc has the boot from usb pendrive option. otherwise no go.

2. xubuntu on a usb pendrive only gives you access to what you have in the pendrive. it is a good option for the small 2gb flash pc, but if you have a hdd inside, no go.

3. for some reason that i don't yet know, my xubuntu on paendrive likes to crash. but probably it's something wrong i did:)

---

### Post by jose158 on 2009-01-24
Ok the flash drive did boot using Unetbootin, but when I try to install it on the Compact Flash, I get: ```
The creation of swap space in partition #5 of SCSl1 (0,0,0) (sda) failed
```

---

