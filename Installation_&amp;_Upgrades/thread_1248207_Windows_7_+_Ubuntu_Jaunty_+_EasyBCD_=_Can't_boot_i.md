---
title: "Windows 7 + Ubuntu Jaunty + EasyBCD = Can't boot into Ubuntu?"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by chris82thekid on 2009-08-23
Hello, I have been using Ubuntu through LiveCDs and Wubi for a while and decided to try a full install. I used UNETBOOTIN to make a bootable USB drive. I uninstalled the Wubi install from Windows, then booted from the USB drive into a live session of Ubuntu. I then followed this guide:

[Ubuntu - NeoSmart Technologies Wiki]("http://neosmart.net/wiki/display/EBCD/Ubuntu") 

That is, I made an ext3 partition for Ubuntu itself, and a swap partition for the OS--Windows 7 is the first partition on the drive, the swap is the second, and Ubuntu is 3rd.

I installed GRUB to Ubuntu's partition (/dev/sda3) so I could use Windows' bootloader.

Then I rebooted, and since 7 didn't know that Ubuntu existed, I opened EasyBCD and added an entry for Linux, selecting the Linux primary partition. After saving to the mbr I rebooted and was presented with the Windows bootloader with these options:

Windows 7
Ubuntu

When I chose Ubuntu, I got this:
```

BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant http://www.winimage.com/bootpart.htm

Loading new partition

Bootsector from C.H. Hochst„tter

 Cannot load from harddisk.

Insert Systemdisk and press any key.

```Which isn't coming from GRUB, it didn't load into GRUB.

What did I do wrong?

---

### Post by stlsaint on 2009-08-23
looks like you did something wrong with install...seem like its looking for the usb that you used to install...try installing from iso on cd instead!!

---

### Post by chris82thekid on 2009-08-23
> **stlsaint said:**
> looks like you did something wrong with install...seem like its looking for the usb that you used to install...try installing from iso on cd instead!!

I don't have any blank CDs to use but why should it matter since the USB drive is acting just like a bootable CD?

EDIT: I would also like to add that in EasyBCD, the Linux drive is set to my hard drive but there is an option "BOOT" should I use that?

---

### Post by stlsaint on 2009-08-23
also ensure that you have used EasyBCD correctly...install grub to ubuntu bootrecord properly...then chainload grub-br to easybcd using bcdedit-tool!!

---

### Post by stlsaint on 2009-08-23
> **chris82thekid said:**
> I don't have any blank CDs to use but why should it matter since the USB drive is acting just like a bootable CD?

EDIT: I would also like to add that in EasyBCD, the Linux drive is set to my hard drive but there is an option "BOOT" should I use that?


well pending my last post it depends on how you are trying to use BCD...easyBCD is not meant to be used with as a booting selection...it mainly holds the bootloader options for you! EasyBCD can be used to do alot of things tho so be careful!

---

### Post by NoBugs! on 2009-08-23
According to the BootPart site:
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
"Bootpart 2.60 is compatible with Windows NT, Windows 2000 and Windows XP."
Have you looked for a newer Windows7 compatible version?

---

### Post by Mark Phelps on 2009-08-25
Couple of comments ...

Notice that the bootpart date is 2005.  There's no way a boot utility written in 2005 is going to handle the entirely new boot loader setups in Vista, and now, in Windows 7.

As to EasyBCD, I didn't catch which version you're using.  The current one is version 2. If you're not using that, go to the NeoSmart Technology forums and download the most current version.  It works better with Windows 7 than the original version (written for Vista).

---

### Post by presence1960 on 2009-08-25
My suggestion is to not use Easy BCD and uninstall it and use GRUB. GRUB is way more configurable and can do a lot more than EasyBCD. besides since you want to learn Linux you might as well start learning the most basic function: getting Linux to boot. Without that your installation is useless.

---

### Post by Pillars of Creation on 2011-03-04
chris82thekid

“I installed GRUB to Ubuntu's partition (/dev/sda3) so I could use Windows' bootloader.  .  . I opened EasyBCD and added an entry for Linux, selecting the Linux primary partition. . .  What did I do wrong?”

See step five under installing Ubuntu from the “Ubuntu - NeoSmart Technologies Wiki” you referenced. This guide refers to the Ubuntu 10.04 TLS release. It clearly states that you should not click on the advanced options and try to install GRUB-2 to a partition. Rather you are supposed to take the default options which will install GRUB-2 to the MBR of hard drive zero. Then you will use the Windows 7 recovery CD to restore the boot to Windows 7. Once you can boot into Windows 7 you can add  the entry to boot into Ubuntu 10.04 TLS. When making the entry you click on the Linux/BSD tab. Click on “type” and from the pull down list select GRUB-2. You will note that there is no option to select a partition. Easy BCD will automatically find the grub.cfg file in the boot/grub partition in the first GRUB-2 based Linux OS and add that boot option to the Easy BCD boot selection list.

When you boot into that OS selection, you’ll be chain loading into GRUB-2, where by default you will boot into Ubuntu 10.04 after a delay. There is an additional procedure to set the time to boot in the GRUB-2 menu to zero if you wish.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Note that where you select where you want to place GRUB-2 during the Ubuntu install process has changed in version 10.10. It is now where it should be where you select hard drive partitioning options rather than towards the end of the install process.

In general setting up a dual-boot between Windows 7 and Ubuntu is really quite simple. Also setting up a triple boot between Windows 7, Windows XP and Ubuntu is also easy. Things get more problematic if you want to run two Ubuntu’s and/or to Windows XP’s on a system. Also using more than one hard drive makes things more difficult.

Note that the current stable release of Easy BCD is version 2.0.2. It has been out since about 08/10/2010 and lacks many features that are in the latest data build. The latest beta build as of today is 2.1-137 and is available at the link below at the NeoSmart support forum. It adds support for installing multiple Linux distributions that use GRUB-1 amongst many other things.

Easy BCD latest beta build:
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

Neosmart Forum:
[http://neosmart.net/forums](http://neosmart.net/forums)

Easy BCD documentation:
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

---

