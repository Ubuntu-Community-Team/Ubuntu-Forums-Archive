---
title: "&quot;Stormy&quot; HDD drive with NTFS + FAT16 + unknown and its broken boot"
date: 2013-02-03
forum: Hardware
---

### Post by ivotkl on 2013-02-03
OK. Quick briefing. A friend of mine lent me an HDD to "play with", which has apparently suffered from an electrical/heavy storm and maybe a discharge. Her husband claims it has 3 partitions but I see only 2 with testdisk (BTW, I am using su privilege). Apparently there are some damaged sectors.

Below you can find information about HDD's damaged boot record. At least it is being recognised, but I've tried mounting it and it ain't working either.

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1 30399 254 63  488375937

filesystem size           488375937 1
sectors_per_cluster       8 0
mft_lcn                   786432 0
mftmirr_lcn               4923918 0
clusters_per_mft_record   -10 0
clusters_per_index_record 1 0
Extrapolated boot sector and current boot sector are different.
```

I'm afraid to overwrite some data on HDD if I create a new MBR or to make it worse. Also, how many sectors does an 250 GB WD Caviar HDD has? I'm not sure if it is listing partition. Apparently it is as it shows partition number 1 Primary and filesystem to be HPFS OR NTFS. I've never used this tool before and I would like to give at least some positive answer to my friend.

Thank you in advanced.

PS: I do not have an equal or higher storage capability HDD to try to "clone" it. Is there any workaround?

PS2: Is this MBR empty?

```
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
 1 P HPFS - NTFS              0   1  1 30399 254 63  488375937
Boot sector                        Backup boot sector
00C0 00000000 00000000   ........  00000000 00000000   ........
00C8 00000000 00000000   ........  00000000 00000000   ........
00D0 00000000 00000000   ........  00000000 00000000   ........
00D8 00000000 00000000   ........  00000000 00000000   ........
00E0 00000000 00000000   ........  00000000 00000000   ........
00E8 00000000 00000000   ........  00000000 00000000   ........
00F0 00000000 00000000   ........  00000000 00000000   ........
00F8 00000000 00000000   ........  00000000 00000000   ........
0100 00000000 00000000   ........  00000000 00000000   ........
0108 00000000 00000000   ........  00000000 00000000   ........
0110 00000000 00000000   ........  00000000 00000000   ........
0118 00000000 00000000   ........  00000000 00000000   ........
0120 00000000 00000000   ........  00000000 00000000   ........
0128 00000000 00000000   ........  00000000 00000000   ........
0130 00000000 00000000   ........  00000000 00000000   ........
0138 00000000 00000000   ........  00000000 00000000   ........
0140 00000000 00000000   ........  00000000 00000000   ........
0148 00000000 00000000   ........  00000000 00000000   ........
0150 00000000 00000000   ........  00000000 00000000   ........
0158 00000000 00000000   ........  00000000 00000000   ........
0160 00000000 00000000   ........  00000000 00000000   ........
0168 00000000 00000000   ........  00000000 00000000   ........
0170 00000000 00000000   ........  00000000 00000000   ........
0178 00000000 00000000   ........  00000000 00000000   ........
0180 00000000 00000000   ........  00000000 00000000   ........
0188 00000000 00000000   ........  00000000 00000000   ........
0190 00000000 00000000   ........  00000000 00000000   ........
0198 00000000 00000000   ........  00000000 00000000   ........
```

```
MFT and MFT mirror are bad. Failed to repair them.
```

---

### Post by ivotkl on 2013-02-04
Shameless bump. Thank you. :)

**EDIT:** I was able to mount 178ish GiB Win Partition, but only folders I see are "System Volume Information" and "Recycle Bin".

---

### Post by Mark Phelps on 2013-02-05
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by ivotkl on 2013-02-06
Thank you so much Mr. Phelps for helping me out. IT was actually better to use windows programs for windows files as it found almost everything in a good state.

> Your data ... your money ... your choice.

I will ask my friend about that and if she agrees, I'll charge her the license.

---

### Post by ivotkl on 2013-02-08
**Marking it as solved.**

Solution: Used a combination of testdisk under Linux to fix some sectors and MBR + partition table of it, then file recovery software under windows to retrieve some files. Not all files are recoverable in my case.

Thank you for the suggestion, Mark.

---

