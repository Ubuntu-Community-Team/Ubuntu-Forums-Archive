---
title: "problems transfering large files"
date: 2008-08-15
forum: General Help
---

### Post by Jh60082 on 2008-08-15
Hi there! Im a serious linux and ubuntu newbie, but im getting it! Anyway, im am trying to transfer files from one of my hard drives to an external drive i bought. Anyway when I transfer large folders ubuntu just decides to stop, i was reading about it on other posts but i got really lost. Anyway, i will be willing to anything that will help the transfer go better. thank you!!

---

### Post by stoneage on 2008-08-15
How gig are the files and how is your external formatted?
I remember reading somewhere that you cannot transfer files over 4Gb with NTFS

---

### Post by Too Late on 2008-08-15
FAT32 has the 4 GB limit, not NTFS.

So what filesystem does your external drive have?

---

### Post by Jh60082 on 2008-08-15
woo hoo people wrote back! My external hard drive is formatted in the NTFS format, and i would like to keep it that way since im moving files from my windows hard drive to a new windows hard drive.

---

### Post by stoneage on 2008-08-16
> **Too Late said:**
> FAT32 has the 4 GB limit, not NTFS.

So what filesystem does your external drive have?

Woops! Apologies to you both - I need to get my memory checked.

Thanks for the correction Too Late.

---

### Post by unutbu on 2008-08-16
Jh60082, do you find that transferring small files works fine, but the copying speed for large files is dramatically slower? If so, you might be experiencing this bug:

slow IDE performance with large files: [http://bugs.launchpad.net/ubuntu/+bug/238788](http://bugs.launchpad.net/ubuntu/+bug/238788) [http://bugs.launchpad.net/ubuntu/+bug/216878](http://bugs.launchpad.net/ubuntu/+bug/216878)
[http://bugs.launchpad.net/ubuntu/+bug/155511](http://bugs.launchpad.net/ubuntu/+bug/155511)

---

### Post by Jh60082 on 2008-08-16
Thank you for the help everyone, those sites that you sent me unutbu were quite confusing! can someone help me with those? Oh for reference my external HDD was just recently bought and it is an Iomega Presitge 500 GB in the NTFS format. and my Other HDD is a Western Digital 200 GB also in the NTFS format. If anybody needs me to post outputs of commands in the terminal i can do that as well.

---

### Post by unutbu on 2008-08-16
Jh60082, when you transfer a large file, does the copying stop before it is completed or does the copying drag on very slowly, or does your whole computer hang?

And are both the Iomega and Western Digital external hard drives? Is Ubuntu on a third hard drive?  

Please post the output of 
```

sudo fdisk -l 
mount
```

---

### Post by Jh60082 on 2008-08-17
My Iomega is an external hard drive, my Western digital is internal, it came with the system i bought three years ago. Ubuntu is running on a third hard drive (the one that is 20 GB that shows up in sudo fdisk -l output) The drive that appears as 2029 MB is my flash drive i happen to have plugged in at the time, it is also called JEREMIAH for references to the output of mount.

Speaking of which, here is the outpost of fdisk:

```
jeremiah@hdsn01:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20411080704 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb3334e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2372    19053058+  83  Linux
/dev/sda2            2373        2481      875542+   5  Extended
/dev/sda5            2373        2481      875511   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         196     1574338+  83  Linux
/dev/sdb2   *         560       24320   190860232+   7  HPFS/NTFS

Disk /dev/sdg: 2029 MB, 2029518848 bytes
17 heads, 32 sectors/track, 7286 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        7287     1981936    6  FAT16

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89d8988e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       60801   488384001    7  HPFS/NTFS

```



and here is the output of mount:

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jeremiah)
/dev/sdb2 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdg1 on /media/JEREMIAH type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdh1 on /media/Iomega_HDD type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

### Post by Jh60082 on 2008-08-17
Oh i forgot to mention, when i am copying large folders with different sized files, ubuntu starts to transfer then just stops and the light on the external hard drive stops and shows to activity, i can do other things on the computer but it just stop copying.

---

### Post by unutbu on 2008-08-17
Does anything get copied, or is it a total bust?

Also, perhaps try this:

Suppose SRC is a path to a source directory (on the Iomega) and TARGET is a path to a target directory (on the Western Digital). Type
```

cp -a --verbose SRC/* TARGET
```
Hopefully the --verbose flag will encourage cp to give us a clue why the job is failing.

---

### Post by Jh60082 on 2008-08-18
should i be typing it in like this? ```
cp -a --verbose /media/Iomega_HDD/* /
``` Or how should i be typing it in.

---

### Post by Jh60082 on 2008-08-18
Oh wow, so i finally figured it out, here is the entire script it ran, im pretty sure there was more in the beginning but it didn't show in the terminal, anyway, hope this helps
```
/Office/Recent/Order of operations.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Order of operations.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Presentation finished666.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Presentation finished666.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Presentation1.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Presentation1.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Prolouge.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Prolouge.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/ReadmeUSA.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/ReadmeUSA.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Resume_Janetta_Henderson.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Resume_Janetta_Henderson.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Rio Rancho Cyber Academy Membership Form View.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Rio Rancho Cyber Academy Membership Form View.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/RR 2008 online order form(2).LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/RR 2008 online order form(2).LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/RR 2008 online order form.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/RR 2008 online order form.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Science.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Science.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Select-a-language birthday card.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Select-a-language birthday card.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Strong acid.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Strong acid.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Student Council Meeting Dates View.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Student Council Meeting Dates View.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TCDACE.tmp.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TCDACE.tmp.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TCDAEE.tmp.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TCDAEE.tmp.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Templates.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Templates.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Test Intranet.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Test Intranet.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/test21.html.url' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/test21.html.url'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/The real pookie.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/The real pookie.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/The Sociology Society.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/The Sociology Society.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TMPmhjfmtu2y3.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/TMPmhjfmtu2y3.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/tokens_71557.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/tokens_71557.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/U2L5.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/U2L5.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/US History.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/US History.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/user.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/user.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Viceroyalties.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Viceroyalties.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Welcome.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Welcome.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/WINNERS!.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/WINNERS!.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Word.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Word.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Writing Project.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Writing Project.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/WSCFDepl.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/WSCFDepl.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/XLSTART.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/XLSTART.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/ZALSKTOX.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/ZALSKTOX.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/_private.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/_private.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/default.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/default.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Desktop.ini' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Desktop.ini'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Desktop.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Desktop.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/doc1.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/doc1.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/doc2.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/doc2.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Docs on jeremiah.workspace.office.live.com.url' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Docs on jeremiah.workspace.office.live.com.url'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/egroupware on jjh.url' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/egroupware on jjh.url'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/egroupware.url' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/egroupware.url'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Email.html.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Email.html.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Email.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Email.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/EMMY77 Homepage.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/EMMY77 Homepage.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/English 11.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/English 11.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Epic_Powerpoint_Unit3_Lesson1.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Epic_Powerpoint_Unit3_Lesson1.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Ex2007_pricing_overview.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Ex2007_pricing_overview.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/exchange.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/exchange.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/fghf.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/fghf.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Fundraising thank you card.LNK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Recent/Fundraising thank you card.LNK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/VB11.pip' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/VB11.pip'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Word11.pip' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Word11.pip'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Wordma11.pip' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Office/Wordma11.pip'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.NK2' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.NK2'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.srs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.srs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.xml' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah.xml'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah~1.srs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Jeremiah~1.srs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/outcmd.dat' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/outcmd.dat'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.NK2' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.NK2'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.srs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.srs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.xml' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/Outlook.xml'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/OutlPrnt' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Outlook/OutlPrnt'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/CREDHIST' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/CREDHIST'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/03e94626-1602-4d8d-ae33-d44e7c6d6609' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/03e94626-1602-4d8d-ae33-d44e7c6d6609'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/0f95de42-062e-4ed3-b782-a6f0041e87ec' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/0f95de42-062e-4ed3-b782-a6f0041e87ec'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/1d6269b5-e374-4f95-8a7d-7a585d9a3101' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/1d6269b5-e374-4f95-8a7d-7a585d9a3101'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/22ab00c4-8c01-4250-8de4-d2575941650f' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/22ab00c4-8c01-4250-8de4-d2575941650f'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/36321bbb-493c-4cc8-aa18-24aa3ce608a5' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/36321bbb-493c-4cc8-aa18-24aa3ce608a5'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/48e59a91-6438-4aaa-9dd0-62a0dc327532' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/48e59a91-6438-4aaa-9dd0-62a0dc327532'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/4e22954d-f16f-42f6-aab4-c45db8ab758d' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/4e22954d-f16f-42f6-aab4-c45db8ab758d'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/564e9c5e-c475-47e4-be12-ee9cbcedb4e5' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/564e9c5e-c475-47e4-be12-ee9cbcedb4e5'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/5C9205DE-FF52-4A77-B8A1-6863A09CE1EF' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/5C9205DE-FF52-4A77-B8A1-6863A09CE1EF'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/7aeb05b7-bd67-4b54-ad7c-21b7b3e55ea9' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/7aeb05b7-bd67-4b54-ad7c-21b7b3e55ea9'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/89b9a2d9-cfb8-4a8c-95b5-0632eb8a66eb' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/89b9a2d9-cfb8-4a8c-95b5-0632eb8a66eb'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/9238ad56-2733-4c13-bb5e-8e4c44776fb9' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/9238ad56-2733-4c13-bb5e-8e4c44776fb9'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/aabbc487-7f84-4bad-a02b-bd155400a869' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/aabbc487-7f84-4bad-a02b-bd155400a869'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/ad928795-0a49-4997-a26e-a5886f9d44de' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/ad928795-0a49-4997-a26e-a5886f9d44de'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/b7406367-6a8a-43c3-a627-607a1a0c11df' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/b7406367-6a8a-43c3-a627-607a1a0c11df'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/c29327a5-5bce-45c4-a1f3-95237d8f87b9' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/c29327a5-5bce-45c4-a1f3-95237d8f87b9'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/c8162e9c-b3e0-4e45-a398-5e6b28f83eca' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/c8162e9c-b3e0-4e45-a398-5e6b28f83eca'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/Preferred' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Protect/S-1-5-21-2496668219-3069583374-3992879676-1003/Preferred'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/2F98E15CC0F55F1A31FA6D27B55A2A17F6A98CB1' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/2F98E15CC0F55F1A31FA6D27B55A2A17F6A98CB1'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/31F2B58D66C1E93919814C01B7845166A65F8D4F' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/31F2B58D66C1E93919814C01B7845166A65F8D4F'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/3352E9DE4C9FBAAC2DB38945DC3299A9B3A6FC8A' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/3352E9DE4C9FBAAC2DB38945DC3299A9B3A6FC8A'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/74331DA3BE1CA20D2077ED7246E7EE7180B8A6B2' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Certificates/74331DA3BE1CA20D2077ED7246E7EE7180B8A6B2'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/CRLs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/CRLs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/CTLs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/CTLs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/240CFF6F6B52A2392D3D4702DF32516C9F4D4B38' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/240CFF6F6B52A2392D3D4702DF32516C9F4D4B38'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/5206ABFA5B750933BF1B31A361584E4DABC3F83F' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/5206ABFA5B750933BF1B31A361584E4DABC3F83F'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/AB4428FD2F480F595B20419606F8D2FCCDFAADE0' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/My/Keys/AB4428FD2F480F595B20419606F8D2FCCDFAADE0'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates/4F8CC8F1452CBD17B75E805386377C1CF8891E39' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates/4F8CC8F1452CBD17B75E805386377C1CF8891E39'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates/52673E4564FFE4E1657D0EDF89885682BB77F61F' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/Certificates/52673E4564FFE4E1657D0EDF89885682BB77F61F'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/CRLs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/CRLs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/CTLs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/SystemCertificates/Request/CTLs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/Normal.BAK' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/Normal.BAK'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/Normal.dot' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/Normal.dot'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/~$Normal.dot' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Templates/~$Normal.dot'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows/Themes' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows/Themes'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows/Themes/Custom.theme' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows/Themes/Custom.theme'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Images' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Images'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Images/Verizon.imc' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Images/Verizon.imc'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com/CHOutgoing.dat' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com/CHOutgoing.dat'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com/UserConfiguration.dat' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/jeremiah@hmrq.com/UserConfiguration.dat'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs/msncalllog5.txt' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs/msncalllog5.txt'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs/msncalllog6.txt' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Live Call/Logs/msncalllog6.txt'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger/3357876979' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger/3357876979'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger/3357876979/ListCache.dat' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Windows Messenger/3357876979/ListCache.dat'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/AutoRecovery save of Document4.asd' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/AutoRecovery save of Document4.asd'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/AutoRecovery save of Normal.as$' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/AutoRecovery save of Normal.as$'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/STARTUP' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/STARTUP'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA0004.wbk' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA0004.wbk'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA0845.asd' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA0845.asd'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA1412.asd' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRA1412.asd'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL0003.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL0003.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL0136.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL0136.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL1815.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL1815.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL2795.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL2795.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL3092.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL3092.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL3535.tmp' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Microsoft/Word/~WRL3535.tmp'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/Application Data/Opera' -> `/media/disk/Files/Documents and Settings/Owner/Application Data/Opera'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/ntuser.dat.LOG' -> `/media/disk/Files/Documents and Settings/Owner/ntuser.dat.LOG'
`/media/Iomega_HDD/Files/Documents and Settings/Owner/ntuser.ini' -> `/media/disk/Files/Documents and Settings/Owner/ntuser.ini'
`/media/Iomega_HDD/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/desktop.ini' -> `/media/disk/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/desktop.ini'
`/media/Iomega_HDD/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/Di1' -> `/media/disk/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/Di1'
`/media/Iomega_HDD/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/INFO2' -> `/media/disk/RECYCLER/S-1-5-21-2496668219-3069583374-3992879676-1003/INFO2'
removed `/media/disk/System Volume Information/MountPointManagerRemoteDatabase'
`/media/Iomega_HDD/System Volume Information/MountPointManagerRemoteDatabase' -> `/media/disk/System Volume Information/MountPointManagerRemoteDatabase'
`/media/Iomega_HDD/System Volume Information/tracking.log' -> `/media/disk/System Volume Information/tracking.log'
removed `/media/disk/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/change.log.1'
`/media/Iomega_HDD/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/change.log.1' -> `/media/disk/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/change.log.1'
removed `/media/disk/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/RestorePointSize'
`/media/Iomega_HDD/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/RestorePointSize' -> `/media/disk/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP66/RestorePointSize'
`/media/Iomega_HDD/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP68/change.log' -> `/media/disk/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP68/change.log'

```

---

### Post by unutbu on 2008-08-18
Jh60082,

[list]
[*] You appear to be transferring everything from /media/Iomega_HDD to /media/disk.
Please post the output of 

```
du -sh /media/Iomega_HDD
du -sh /media/disk
```

[*] Can you post the names of some of the files that were not successfully transferred? I wonder if the problem might have to do with spaces or special characters in the path names.

[/list]

---

### Post by Jh60082 on 2008-08-20
Hey that command: cp -a --verbose /media/disk/* /media/Iomega_HDD
transfered all my files!! thanks for the help! however, i do want to continue to solve why i cant just move them with out command line stuff, if you dont mind: here is the outputs:

```
jeremiah@hdsn01:~$ du -sh /media/Iomega_HDD
108G	/media/Iomega_HDD
jeremiah@hdsn01:~$ du -sh /media/disk
105G	/media/disk
jeremiah@hdsn01:~$ 

```

---

### Post by unutbu on 2008-08-20
Jh60082, the "du -sh DIR" command tells us how much disk space DIR takes up.
It looks like 3G are missing from /media/disk (105G) that are on /media/Iomega_HDD (108G).

Hm. Maybe the --verbose flag in "cp -a --verbose ..." spewed out too much output and the useful error messages got lost in the crowd.

How about this: perhaps we can find out what files if any are missing by doing the following:
```

cd /media/Iomega_HDD      # change directory
ls -laR . > ~/Iomega-laR  # dump a listing of /media/Iomga_HDD into a file named Iomega-laR
cd /media/disk
ls -laR . > ~/disk-laR    # dump a listing of /media/disk into a file named disk-laR
cd
diff Iomega-laR disk-laR > diff.txt   # compare the two files, send output to diff.txt
```

Look through diff.txt to see what files failed to get transferred. 
Post a few.
Is there something in common that these files share that other files that did get transferred didn't share?

I am hoping that the problem revolves around a filename with taboo characters in it. Maybe a forward-slash '/' that Windows understood to be part of the filename, but which Linux thinks is a directory separator. 

I understand that you'd prefer using Nautilus, and I agree, you should be able to transfer files with Nautilus. However, there is something strange going on here and I don't know Nautilus well enough to coax it into telling us what the problem is. Perhaps there is no way to do it from within Nautilus. Therefore, let's persist in using the command-line tools until we know what the problem is. 

If the problem turns out to be mal-named files, if we're lucky I might be able to find a bulk-renaming command to remove the problem symbol(s), and after that you should be able to use Nautilus... hopefully. We'll have to find out what the real problem is first.

---

