---
title: "WD Desktop Black 4TB HD not visible."
date: 2013-07-17
forum: Hardware
---

### Post by casbahdk on 2013-07-17
I just purchased a WD Desktop Black 4TB hard disc (SATA 6Gb/s (SATA 3.0), 64MB Cache, 7200RPM, 3.5", Dual processor). I have installed it in my home built tower computer. I can use the cable for the drive to get other drives to work, but I can't take a cable from another drive and get the new drive to show in Ubuntu 12.04, nor will the drive work when I connect it to the cable that came with the drive. It is my understanding that the SATA 3 controller can figure out for itself which channel each drive should run on without manually switching channels. Does this mean that my new drive is faulty?

---

### Post by oldfred on 2013-07-17
Does the drive show in BIOS/UEFI list of drives?

Until it is partitioned and formatted it will not work with any operating system. With a 4TB drive you do have to use gpt partitioning.

You can use gdisk or gparted to partition drive, but have to change from default msdos(MBR).
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by casbahdk on 2013-07-17
Thanks for the quick reply. No, the drive doesn't show up in the UEFI. I have tried plugging the drive into different SATA 3 ports, but that hasn't helped. The UEFI settings have all six of the SATA 3 ports ( 1-4, 5-6) set to AHCI.

---

### Post by oldfred on 2013-07-17
If you have tried different cables & different ports and it still does not show in UEFI as an available drive, then drive does not sound like it is working. 
Seems like a newer computer as you have SATA3 ports but some older systems could not see the new very large drives. Have you updated UEFI/BIOS to latest version?

---

### Post by CharlesA on 2013-07-17
> **oldfred said:**
> If you have tried different cables & different ports and it still does not show in UEFI as an available drive, then drive does not sound like it is working. 
Seems like a newer computer as you have SATA3 ports but some older systems could not see the new very large drives. Have you updated UEFI/BIOS to latest version?

I've seen issues reported with anything that isn't UEFI detecting drives greater than 3TB. @OP: Check the mobo manufactuer's site to see if there is a BIOS upgrade.

Either that or the drive is dead, but it's best to explore all possibilities.

---

### Post by casbahdk on 2013-07-17
I have never tried updating a BIOS (UEFI) before. The BIOS version number is 0705. [This]("http://support.asus.com/download.aspx?SLanguage=en&m=SABERTOOTH%20990FX&os=30") appears to be the correct page, but what do I need? I don't see any dates on the downloadable files / utilities for the BIOS / UEFI. Any ideas? I want to make sure that I don't screw this up. My tower is dual boot Ubuntu 12.04 / Win 7 64-bit.

---

### Post by oldfred on 2013-07-17
You need to review manual to see procedure. I have not done it with new UEFI system.

But my old BIOS had 3 ways to update. One only from Windows with an .exe file, one from a DOS bootable flash drive, and a third where it just read the update file from a flash drive that did not have to be bootable but FAT32 formatted. You need to see which option or options your particular system supports.

---

### Post by CharlesA on 2013-07-17
> **casbahdk said:**
> I have never tried updating a BIOS (UEFI) before. The BIOS version number is 0705. [This]("http://support.asus.com/download.aspx?SLanguage=en&m=SABERTOOTH%20990FX&os=30") appears to be the correct page, but what do I need? I don't see any dates on the downloadable files / utilities for the BIOS / UEFI. Any ideas? I want to make sure that I don't screw this up. My tower is dual boot Ubuntu 12.04 / Win 7 64-bit.

Wow, old BIOS. Might as well put the newest version on there. There should be an Asus EZ flash or something like that so you can update it off a usb stick.

---

### Post by casbahdk on 2013-07-18
Still trying to make a direct Internet connection to an FTP server in ASUS Update  :-( The advantage, if the dwnload would work is that I can make a UEFI backup in case I need to downgrade.

---

### Post by CharlesA on 2013-07-18
You should be able to save a backup image of the BIOS to the flash drive. At least that was how it worked on my older ASUS mobo.

---

### Post by Mark Phelps on 2013-07-18
I used to have ASUS motherboards as well, and used EZ-flash to do BIOS updates.  But that was before the days of UEFI.

The most important thing (in my experience) is to know that you have the ability to do both of the following -- and to know that BEFORE you do the BIOS upgrade:
1) Save off the current, working, BIOS to an external media, most likely, a USN stick
2) Restore the saved BIOS if the update goes badly.

---

