---
title: "Grub overriding BIOS"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by thewang767 on 2009-10-26
I used to have a dual-boot with XP and Linux on two separate drives. Recently, I built an entire new computer, but kept my two hard drives. After everything was put together, the Linux disk booted fine. When I went to boot up from the Windows disk, my machine crashed, due to a corrupt disk I'm guessing. I want to reinstall XP, but Grub isn't letting me boot from a CD or flash drive.

I installed Linux after my existing XP installation; and now if I disconnect my Linux drive, I am not able to boot up. After the BIOS loads, my XP disk tries to load Grub (I don't know why) and returns Error 17.

I've tried inserting an XP cd in, but the BIOS doesn't boot from the CD. I also tried booting from a USB drive that had Ubuntu on it to try to wipe the XP disk.

Does anyone have any solutions?

---

### Post by Herman on 2009-10-26
:) You might need to take a look at the cables and jumper settings you're using to plug your drives in with if they're IDE drives, including your CD/DVD drive, if it's IDE it'll have jumper settings too.

If you have SATA drives, take a look at the port numbers you have them plugged into.

Another way to change your drive order around without opening your case and unplugging any cables in most computers is to play around with the hard disk boot priority in the BIOS. Not the boot order, but the hard disk order, this over-rides the port numbering where you plugged them in and can help if you have an IDE/SATA  BIOS numbering priority difference. (If you have some SATA and some IDE drives).

If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the balack plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable. :)

---

### Post by Herman on 2009-10-26
One other thing I just thought of - Windows might not work in a different computer than the one it was originally installed and registered in, I'm not sure, only guessing.  It might have built in anti-piracy mechanisms to disable it if you try to use it in a different PC. One more reason why everybody should forget about proprietary operating systems and switch to open source. :)

---

### Post by sandy8925 on 2009-10-26
You're right Herman it does have such mechanisms. From what I've heard if you change more than 5 components it gets disabled and you have to register it again or something. (I've had this problem before when I changed a few things. But not as drastic as a new motherboard or moving to another comp.)

---

### Post by cupzhangteng on 2009-10-26
> **thewang767 said:**
> I used to have a dual-boot with XP and Linux on two separate drives. Recently, I built an entire new computer, but kept my two hard drives. After everything was put together, the Linux disk booted fine. When I went to boot up from the Windows disk, my machine crashed, due to a corrupt disk I'm guessing. I want to reinstall XP, but Grub isn't letting me boot from a CD or flash drive.

I installed Linux after my existing XP installation; and now if I disconnect my Linux drive, I am not able to boot up. After the BIOS loads, my XP disk tries to load Grub (I don't know why) and returns Error 17.

I've tried inserting an XP cd in, but the BIOS doesn't boot from the CD. I also tried booting from a USB drive that had Ubuntu on it to try to wipe the XP disk.

Does anyone have any solutions?
In my opinion,one simply way to solve the problem is that you can get the BIOS battery on your mainboard first,then you set it up again after seconds.Maybe it will be OK!

---

### Post by Mark Phelps on 2009-10-26
> **thewang767 said:**
> ... When I went to boot up from the Windows disk, my machine crashed, due to a corrupt disk I'm guessing. ... Does anyone have any solutions?

Sounds like what you did was remove a drive containing an MS Windows installation from one machine and simply plug it into another machine? Right?

Unless the second machine is virtually identical to the first in terms of hardware, THAT WILL NOT WORK!

Basically, you're crashing because when MS Windows boots, it tries to load your OLD drivers -- the ones for the old machine --, those loads fail, and the machine crashes.

There have been cases where folks have been able to fix this problem by first, uninstalling all third-party drivers on the old machine, second, moving the drive to the new machine, third, booting the new machine, connecting to Windows Update, and letting it find an install new drivers.

This only works if the default MS drivers are good enough to allow the machine to boot into MS Windows and run Windows Update.

Even THEN, unless you have a retail license of XP, there's still the possibility that, once you get the MS Windows OS working, it will discover enough hardware changes that it will deactivate itself.  If that happens, you will have to telephone MS Support and try to convince them to issue you a new license key.

So, as you can tell, MS Windows was not designed to be easily migrated from one machine to another.

---

### Post by raymondh on 2009-10-26
> **Mark Phelps said:**
> 
 If that happens, you will have to telephone MS Support and try to convince them to issue you a new license key.


Yup .....

---

### Post by presence1960 on 2009-10-26
> **sandy8925 said:**
> You're right Herman it does have such mechanisms. From what I've heard if you change more than 5 components it gets disabled and you have to register it again or something. (I've had this problem before when I changed a few things. But not as drastic as a new motherboard or moving to another comp.)

You most likely have an OEM version of windows which ties that install to the hardware on the machine when you installed it. I had to call and have it activated when I switched out a hard disk.

---

### Post by atirox on 2009-10-26
Just as a warning before you read what I have to say, you should know that I am completely new to the Linux environment. If this was a Windows environment, I'd be right at home, but it isn't, so please take everything I say concerning Linux with a grain of salt.

Pardon my noobish-ness, but it sounds like what herman said. The BIOS is loaded before the boot loader. If you tell the BIOS not to look in any hard drives for bootable media, it wont find GRUB, and therefore, wont boot into Linux or XP. Also, the reason why it returns the error, is because it cant find GRUB its self. The instructions in the boot sector of your drive tell it to look for grub in the specified location. When you disconnect the drive housing grub, it can no longer find grub, and therefore, gives you the error.

Also, if you reinstall XP, you will no longer have grub as your boot loader, and you'd need to reconfigure it.

---

### Post by oldfred on 2009-10-26
I am surprised presence did not ask you to run script. It seems you still have the grub boot loader on your windows drive, so you do not even get to the point where windows complains about the system not being the original install. If so, you need to first reinstall the windows boot into the MBR of the windows drive. Since the windows drive is normally the first drive when you installed Ubuntu it overwrote the windows boot in the first drive. 
I replaced power supply, motherboard and video card, but not cpu nor harddrives and my system booted but then windows would not finishing loading drivers without the message that I had to phone home & get permission to run system. The other problem was the window error was under all the other windows that were trying to connect to the internet and would not close to let me reauthorize it. It finally worked for me.
If you have the XP disk you can reinstall the MBR from the repair menu with FIXMBR c:. Or download supergrub or on Hermann's site is futher info on fixing or repairing windows installs with testdisk:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by wnderinguy34 on 2009-10-26
The Win installation is moot ,he is trying to boot to the CDROM and it isn't working .More of a hardware issue than OS/software.


thewang767,

make sure the CDROM is the first boot device in BIOS menu.
If the CD is spinning up but not initializing the Windows install ,try disabling both HD and see if the CDROM is even reading the disk.Is it possible this CD isn't bootable,try it in a known good machine.


GRUB isn't over riding the BIOS (it can't) The only reason you are getting to GRUB is 
the cdrom isn't recognized by the BIOS  
wrong boot order of devices
WINXP CD is damaged or isn't bootable.

---

### Post by thewang767 on 2009-10-26
Thanks for the responses. Okay here goes:

0) I tried the motherboard battery first before I bought my new setup. Didn't work.

1) I have two SATA drives (one that came shipped from Compaq with XP, and another I bought and installed Linux on). My CD drive is connected via an IDE cable.

2) I figured that Windows would automatically crash when I changed my entire setup. I think phoning Microsoft will be a waste of time, so I was just going to reinstall XP using my existing CD key? I hope that works, because I *do* have a legit license for Windows.

3) That would overwrite Grub as the default bootloader, but I can go into Windows and write the Linux into the MBR, then install Grub again or whatever.

4) So last night I tried to uninstall Grub (which was on my Windows disk). I did:
```
[FONT=Verdana]dd if=/dev/zero of=/dev/sda bs=446  count=1[/FONT]
```That, I'm assuming, deleted my bootloader for everything, so now I can't even boot Linux. (That was my own fault.)

5) It could be that the XP CD is not bootable, but I tried it on my roommate's computer and it worked fine. I also wasn't able to boot from a USB drive containing Ubuntu either...

> If the CD is spinning up but not initializing the Windows install ,try disabling both HD and see if the CDROM is even reading the disk.Is it possible this CD isn't bootable,try it in a known good machine.I set my boot priorities as CD/DVD, USB-FDD, CD/DVD once and it still didn't boot. I'll try again tonight with a different CD.

---

