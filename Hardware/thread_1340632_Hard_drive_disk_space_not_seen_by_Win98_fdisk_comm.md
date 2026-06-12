---
title: "Hard drive disk space not seen by Win98 fdisk command"
date: 2009-11-28
forum: Hardware
---

### Post by nkao on 2009-11-28
Hi,
I need help to get back the missed 140G hard disk space after I deleted ubuntu 9.10 (upgraded from 9.04) and reclaimed the whole hard disk (149.05GB as shown on gparted screen) using "gparted" when running ubuntu 9.04 from a USB startup disk.
 
However, I am able to boot my Acer AspireOne via an external DVD drive with an Win98 dos bootable CD. But I found there is only around 20GB seen by dos "fdisk" command. After created primary partition (~ 20GB) in "fdisk", I could format the "c:" drive with ~152GB space.
 
Then, I tried to install WinXP onto this hard drive, I got the blue screen saying that there could be virus and need to run "CHKDSK" to check.
 
Please advise me how to get back the whole hard disk space and to start it over again (WinXP with 70GB space, then ubuntu 9.10 or 9.04 with 90GB space)
 
Thanks

---

### Post by adalal on 2009-11-28
> **nkao said:**
> Hi,
I need help to get back the missed 140G hard disk space after I deleted ubuntu 9.10 (upgraded from 9.04) and reclaimed the whole hard disk (149.05GB as shown on gparted screen) using "gparted" when running ubuntu 9.04 from a USB startup disk.
 
However, I am able to boot my Acer AspireOne via an external DVD drive with an Win98 dos bootable CD. But I found there is only around 20GB seen by dos "fdisk" command. After created primary partition (~ 20GB) in "fdisk", I could format the "c:" drive with ~152GB space.
 
Then, I tried to install WinXP onto this hard drive, I got the blue screen saying that there could be virus and need to run "CHKDSK" to check.
 
Please advise me how to get back the whole hard disk space and to start it over again (WinXP with 70GB space, then ubuntu 9.10 or 9.04 with 90GB space)
 
Thanks

I'm not entirely sure what happened, but am I safe to assume that you did indeed convert the Ubuntu 9.10 partition back to fat16/fat32? If it's still in ext/ntfs, win98 would probably not pick it up.

If nothing works, you could load a GParted Live USB, and try reformatting the entire HD.

Best of luck.

---

### Post by nkao on 2009-11-28
> **adalal said:**
> If nothing works, you could load a GParted Live USB, and try reformatting the entire HD.
 
I used "gparted" to re-create the fat32 format primary dos partition, do I need to run "format" command to complete the partition creation in Ubuntu?

---

### Post by u.b.u.n.t.u on 2009-11-29
> **nkao said:**
> Hi,
(WinXP with 70GB space, then ubuntu 9.10 or 9.04 with 90GB space)
 
Thanks

Consider formatting the entire HDD as NTFS. When you boot with your XP CD, there should be an option for that.

[http://support.microsoft.com/kb/313348](http://support.microsoft.com/kb/313348)

Once you have XP installed, then you can install Ubuntu.

I use Windows 7 NTFS with Ubuntu 9.10 ext4 installed via Wubi. You can however install Ubuntu directly via CD. Either way, you can change the partition size.

---

### Post by nkao on 2009-11-30
Thanks for the advise.  I will try your recommendation once I successfully get back the 160G and install WinXP first.
 
Best regards,

---

### Post by nkao on 2009-12-08
Hi,
I tried to use XP install CD to boot my netbook, but it turned out the Windows XP installation procedure stopped due to it detected a hard drive format inconsistant problem.
 
I as restating my problem below with actions what I had done previously.  Hope this is helpful for you to understand what I did and provide solution to me.  Thanks.
 
=======================================================

I need help to reclaim the whole 160GB hard disk space to reinstall Windows XP onto my netbook.

I has an Acer AspireOne netbook with 160GB HD. It had Windows XP installed when I bought it and, two months later, I erased the Win XP entirely by installing Ubuntu 9.04 with the whole HD's 160GB.

3+ weeks earlier, I erased Ubuntu from the hard drive and tried to install Window XP back. The works that I had done are listed in the following:
1. I booted up this netbook using SystemRescureCD and formated the hard drive (with **gparted**) to a primary bootable partition with 149.05GB space in FAT32 format. I also used Ubuntu 9.04 liveCD/USB disk to partition the hard drive in the same way as what I did using SystemrescureCD.

2. I booted up the netbook with a MS-DOS bootable disk (from Win 98), then I run **fdisk** command and there was no such primary partition that I created in **step 1** and when I tried to create a primary partition to this disk, there was only 2.055GB shown as available disk space.

3. I tried to skip step 2 and directly installed Windows XP from the installation CD, but after loading the drivers, the **blue screen** shown and prompted me to check hard disk using **CHKDSK** command.

Please advise me how to reclaim the disk space for Windows XP installation.

I will tried to have Ubuntu installed after Windows XP.
======================================================

---

### Post by nkao on 2009-12-17
Hi,
I tried to boot this netbook with freedos via a USB disk, then I ran spfdisk to create brand new partition for the 160G HD in the netbook with the following details:
1. active and bootable
2. size -- 149.05GB 
3. System_ID -- 0c (zero-c)
4. File_system -- DOS FAT32(LBA)
 
I saved the new partition table, formatted this HD, rebuilt the MBR (in spfdisk), and then exited to DOS. Then I could copy files to the new HD from C: drive to the "D:" drive, where freedos USB flash disk was the "C:" drive. I typed "dir/w D:" and it showed me there are 152,587MB free on the D drive.
 
After that, I rebooted my netbook with a Windows XP install CD, then the system crashed (the blue screen came out) with information saying that there could be virus or inconsistency existed on my hard drive and asked me to run "CHKDSK /F" to verify the cause.
 
Please advise me how you would solve this issue and help me to bring back the HD space to install Windows XP again.
 
Thank you.

---

### Post by nkao on 2010-01-01
Hello,
After a few tries, I realized that the problem could be the XP installation disk that I used did not have SATA driver to support the new SATA hard disk drive. 
 
So I changed to use the backup system disks that were created by Acer's backup program, to restore the Windows XP system.
 
First, I formatted the whole hard disk space (149.0?GB) to NTFS format using gparted in freedos.
 
Second, I made it primary and bootable. 
 
Third, I made a blank MBR by spfdisk.
 
And the last, I used my previous backup system disks (created by running the backup program from Acer) to recover the Windows XP system.
 
Now, my issue had been resolved and the Windows XP was back.
 
Anyway, thanks for your attention.

---

