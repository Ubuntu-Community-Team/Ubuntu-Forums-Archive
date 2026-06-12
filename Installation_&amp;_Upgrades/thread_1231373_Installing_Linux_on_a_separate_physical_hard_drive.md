---
title: "Installing Linux on a separate physical hard drive"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by alh2354@comcast.net on 2009-08-04
[FONT=Arial Narrow]I tried installing Ubuntu 9.04 for the first time-I am currently running a dual boot of Vista and XP on a WD SATA HDD(running as IDE)-call that Disk 0. I also had several other partitions on the SATA HDD containing documents, images, and so on. I also have a 250 GB WD IDE HDD(call that Disk 1) which at the time was blank and unformatted. I decided to install Ubuntu to Disk 1. The mistake I made was the following: I changed the HDD boot order in the bios to boot from Disk 1 first. I then booted to the Linux install disk and proceeded with the installation, which went fine. I had thought that when I rebooted, it would boot Linux from Disk 1-instead it found no operating system. I then changed the HDD boot order in the bios back to the way it had been- Disk 0, the SATA HDD listed first. I was then given the option of booting into Linux or choosing the Vista bootloader, which then enabled me to boot into Vista or XP as I had always done. So what’s the problem ?[/FONT]
[FONT=Arial Narrow]From within Vista, some of the partitions on Disk 0 (all formatted as NTFS) were not visible. Disk management showed the XP, Vista, and documents partitions. The rest was listed as free space and I couldn’t access the files. Fortunately, from within XP all of the partitions on Disk 0 were visible. However, both Partition Magic and Easeus Partition manager listed Disk 0 as bad, and none of the partitions were shown. Thus I cannot work with the free space on Disk 0. From within Linux, Disk 0 is just shown as all free space. [/FONT]
[FONT=Arial Narrow]What I don’t completely understand is why the Ubuntu installer would mess with any of the partitions on Disk 0 when Ubuntu was installed to Disk 1. Is it because I changed the HDD boot order in the bios to boot from Disk 1 first ? [/FONT]

---

### Post by cariboo on 2009-08-04
I sounds like one or more of your ntfs partitions were unmounted improperly, run windows chkdsk on the partitions that don't show up.

---

### Post by alh2354@comcast.net on 2009-08-04
[SIZE=2]Thanks for the reply. I can mount the NTFS partitions from within Linux-that is not my problem. The problem is that I cannot work with the free space on Disk 0 from within Vista or from within XP because the whole 500 GB is listed as a bad partition. I will probably have to wipe everything(I have images of XP and Vista, so I can easily reinstall) and start over. If I partition manually and install the Ubuntu boot loader to Disk 1, which does **not** contain XP or Vista, then should I change the HDD boot order in the bios to boot from Disk 1 first after running the linux installation from the CD ?[/SIZE]

---

