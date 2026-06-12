---
title: "Samsung SSD EVO and EVO 840 slow performance fixed with firmware upgrade"
date: 2014-11-05
forum: Hardware
---

### Post by thewizardz on 2014-11-05
Hi All,

I just wanted to share something I found recently for owners of SSDs Samsung **840 EVO** and Samsung **840 EVO mSATA**. I have a Galago that I purchased with the EVO 840, and I saw a post in the System 76 section here, but I thought I could share in the global Hardware section for everyone else.

Basically, there is a bug in earlier firmwares that cause the performance to degrade over time; Using the "disks" utility in Ubuntu you can do a Benchmark of your SSD and find out if the performance has degraded (it should be an average read speed above 500MB/s). If you experience slow performance then update using the firmware and procedure provided by Samsung. I upgraded mine without any issues, but is always a good practice to do a full backup before doing the firmware upgrade.

I read this for the first time here: [http://www.computerworld.com/article/2836082/samsung-delivers-fix-for-ssd-slowdowns.html](http://www.computerworld.com/article/2836082/samsung-delivers-fix-for-ssd-slowdowns.html)
and this is the website to download the drivers: [http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html)

Pablo

---

### Post by QIII on 2014-11-08
Not sure how you got this done, as neither image actually runs.  The .exe is flawed and throws exceptions.

Inasmuch as this chafes me... I thought I'd share what I'm seeing with anyone who has an one of these drives on their machine ...

[ATTACH=CONFIG]257818[/ATTACH]

I'll send this along in my nastygram to Samsung.

---

### Post by thewizardz on 2014-11-10
I got the ISO burned to a DVD and booted from there; In the section **Samsung SSD 840 EVO Performance Restoration Software** -> Dos version for MAC, Linux users, I downloaded the Version 1.0 (3.21MB) (ISO CD-ROM image),
specifically this link: [http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso](http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso)
I tried the Bootable USB disk but it didn't work for me, but the ISO worked fine.

I'm reading the paragraph again and I realize I made a mistake in my original post. The firmware applies to these models: **840 EVO and 840 EVO mSATA**, though I see in that page there are firmware upgrades for other non-EVO models but I'm not sure if it actually restores the performance.

---

### Post by Pete7874 on 2014-11-12
> **QIII said:**
> Not sure how you got this done, as neither image actually runs.  The .exe is flawed and throws exceptions.

It worked fine for me.  I created a bootable USB stick with FreeDOS, and copied the contents of samsung performance restoration utility to it, and then booted from it.  perf.exe fired up and completed the task without any errors for me.

---

### Post by QIII on 2014-11-13
From what I have been able to ascertain, my issue stems from the fact that I am using an AMD chipset, which is apparently problematic for the update utility.  That's completely unacceptable, of course.

I am engaged in an email conversation with Samsung in an attempt to determine what can be done to affect this update for those who have AMD hardware.  My hope is that this conversation will end up with a solution rather than a "Too bad, so sad!" from them.

At that point my personal solution will be to pop the drive into an Intel machine temporarily and run the USB version of the utility to fix my own drive.  But that is not a satisfactory solution for those who don't have the resources to do that.

So if anyone is using an 840 EVO SSD with an AMD chipset, stay tuned.

---

### Post by Friedolin_K on 2014-12-14
> **thewizardz said:**
> I got the ISO burned to a DVD and booted from there; In the section **Samsung SSD 840 EVO Performance Restoration Software** -> Dos version for MAC, Linux users, I downloaded the Version 1.0 (3.21MB) (ISO CD-ROM image),
specifically this link: [http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso](http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso)
the ISO worked fine.

Hi, I have partionated my  **Samsung SSD 840 **into ntfs and ext4 and use ubuntu besides Windows 8.1. I plan to update my SSD 840 in the same way as  thewizardz did. Does anybody believe that this is Ok?

Thank you for any answer, Friedolin_K

---

### Post by Friedolin_K on 2014-12-17
In fact, I did not found in the net the report of any user who successfully upgraded a partionated ssd with the Samsung restoration software (though the DOS version should be independent of any operating system).

My ssd 840 has three partitions: ntfs, ext4 und linux-swap.  

I believe, the only possibility is as follows:

1. Uninstall ubuntu
2. Restore the original state of the ssd
3. Upgrade the ssd (under windows 8.1)
4. Re-partionate the ssd
5. Reinstall ubuntu

Or anybody knows another possibility?

Friedolin_K

---

### Post by Friedolin_K on 2014-12-18
Does anybody read this forum?

---

### Post by thewizardz on 2014-12-20
Hi Friedolin_K

my disk has an ext4 and a swap partitions, and the software only identifies the disk itself, not the partitions. I dont think there should be a problem, but I strongly suggest you do a full backup of your system before running the software. In any case, your procedure seems like the safest option if you dont want to take any risks..

---

### Post by Friedolin_K on 2014-12-22
Hi[[COLOR=#000000] thewizardz[/COLOR]]("http://ubuntuforums.org/member.php?u=617808"), 

thank you very much for your answer. I believe that I shall be brave and apply the Samsung ISO to the partitioned disk. The "safe procedure" is very elaborate...

Have you any hint for the full "backup of the system"? My Samsung EVO 840 contains ***only*** the two operating systems, Windows 8.1, ubuntu and the boot lader. All my dates and even the ubuntu /home directory are on another hard disk. Is it possible to backup the ssd completely  and to restore it - if necessary - in such a way that both operating systems work again? You see that I am not an expert...

Friedolin_K

---

### Post by thewizardz on 2014-12-22
Maybe try clonezilla: [http://clonezilla.org](http://clonezilla.org) or check this article [http://www.tecmint.com/linux-disk-cloning-tools/](http://www.tecmint.com/linux-disk-cloning-tools/)

---

### Post by Friedolin_K on 2014-12-24
Thank you. This software is exactly what I was looking for.

Merry christmas. Friedolin_K

---

### Post by Friedolin_K on 2014-12-27
Clonezilla worked fine.

> **thewizardz said:**
> I got the ISO burned to a DVD and booted from there; In the section **Samsung SSD 840 EVO Performance Restoration Software** -> Dos version for MAC, Linux users, I downloaded the Version 1.0 (3.21MB) (ISO CD-ROM image),
specifically this link: [http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso](http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_Performance_Restoration.iso)
I tried the Bootable USB disk but it didn't work for me, but the ISO worked fine.

The ISO did not boot on my computer. Unfortunately, I could not disable the UEFI boot-modus. I believe that the Samsung ISO does not boot in UEFI modus.

> **Pete7874 said:**
> I created a bootable  USB stick with FreeDOS, and copied the contents of samsung performance  restoration utility to it, and then booted from it.  perf.exe fired up  and completed the task without any errors for me. 
The bootable USB stick (created with UNetbootin) worked also for me without any problem. The partitioned Samsung ssd (ntfs, ext4 and swap partition) was restored within 20 minutes.

---

