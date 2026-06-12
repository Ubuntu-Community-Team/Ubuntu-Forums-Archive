---
title: "PC not booting, Live CD not detected"
date: 2014-08-01
forum: Hardware
---

### Post by laddtm on 2014-08-01
So, a couple of months ago I was playing TF2 on my somewhat newly built PC. All of a sudden, it stops working, completely. Came back a couple of months later as I need to use my PC now ASAP, and I can't get it to boot. (The PC uses Windows 7) I heard about using Ubuntu to recover files from a PC that won't boot, and when I try to use the CD I downloaded Ubuntu onto, it won't show up or boot with it. I tried it on my other PC, and it booted with the disc in Ubuntu, so I am sure it isn't the disc. I don't know whats wrong, is it a hardware issue? The PC will just boot up into startup repair or start normally, and if I start normally, it blue screens for a split second then resets the PC. I can't find any way to get Ubuntu to work on it, is it because I am having a hardware issue, or is there a BIOS command I can use to launch it, or what?

---

### Post by oldfred on 2014-08-01
Newer system? Is it UEFI or BIOS?

What are hardware specs? Motherboard, processor, video card/chip?

Often boot parameters are prequired with many video cards. But some systems require other boot parameters instead or in addition.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you get grub menu on LiveDVD/Flash drive installer then that is UEFI mode. How you boot installer is how it would install. And best to have Ubuntu in some mode as Windows either both BIOS or both UEFI.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

### Post by laddtm on 2014-08-02
Sorry for being vague, it is UEFI I believe, and here is a list of the specs. Also I have had it for about 6 or so months.
[http://pcpartpicker.com/b/6wTWGX](http://pcpartpicker.com/b/6wTWGX)

---

### Post by oldfred on 2014-08-02
With UEFI you need to make sure secure boot is off. If you installed Windows 7 using defaults from DVD it probably is in BIOS boot mode with MBR(msdos) partitions. You have to convert Windows 7 DVD to flash drive and add a few things to make it a UEFI installer. How installer boots is how it installs.

So you want to boot Ubuntu in BIOS boot mode not UEFI. And with a nVidia card you need nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

With MBR you have the 4 primary partition limit, so you need to allocation one primary partition as the extended partition and install Ubuntu as logical partitions in the extended.
But if Windows is broken you may have troubles. Gparted or installer may not see NTFS partition(s) if chkdsk needed or hibernated. And you should only use Windows 7 to shrink the NTFS partiton or else you may corrupt it further.

After install and any boot before installing the proprietary nVidia driver, you will also need nomodeset. But that is added differently at grub menu.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

