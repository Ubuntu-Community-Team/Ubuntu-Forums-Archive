---
title: "[SOLVED] Fixing a bad NTFS partition using Ubuntu"
date: 2008-09-22
forum: General Help
---

### Post by K0NY on 2008-09-22
Hello all, thanks in advance for your help. These forums are fantastic. After searching around for a bit, I decided to post since I can't seem to find an answer.

I'm running a dual-boot of Ubuntu and Vista. I installed Vista first then Ubuntu so GRUB was managing my choices at start-up. The 115GB Maxtor HDD on which both of these OSes live, is partitioned into 4 slices. 

Yesterday, in a fit of frustration when Vista froze yet AGAIN, I hard-rebooted the PC. When it came back on, it wasn't finding the primary boot partition. GRUB doesn't show at all. I tried repairing the MBR with TESTDISK and the Vista disc's "Window's Repair" to no avail.

GParted sees all the partitions, but can't mount the NTFS partition with Vista on it. I tried using it to scan and repair, but the operation failed with multiple "cluster accounting failed" errors I'm posting the details below.

```
GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (ntfs) on /dev/sda1  00:07    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 2048
end: 158199807
size: 158197760 (75.43 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:07    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80997249536 bytes (80998 MB)
Current device size: 80997253120 bytes (80998 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 119725 (0x1d3ad): missing cluster in $Bitmap
Cluster accounting failed at 119726 (0x1d3ae): missing cluster in $Bitmap
Cluster accounting failed at 119727 (0x1d3af): missing cluster in $Bitmap
Cluster accounting failed at 119728 (0x1d3b0): missing cluster in $Bitmap
Cluster accounting failed at 119729 (0x1d3b1): missing cluster in $Bitmap
Cluster accounting failed at 119730 (0x1d3b2): missing cluster in $Bitmap
Cluster accounting failed at 119731 (0x1d3b3): missing cluster in $Bitmap
Cluster accounting failed at 119732 (0x1d3b4): missing cluster in $Bitmap
Cluster accounting failed at 119733 (0x1d3b5): missing cluster in $Bitmap
Cluster accounting failed at 119734 (0x1d3b6): missing cluster in $Bitmap
Cluster accounting failed at 119735 (0x1d3b7): missing cluster in $Bitmap
Cluster accounting failed at 119736 (0x1d3b8): missing cluster in $Bitmap
Cluster accounting failed at 119737 (0x1d3b9): missing cluster in $Bitmap
Cluster accounting failed at 119738 (0x1d3ba): missing cluster in $Bitmap
Cluster accounting failed at 119739 (0x1d3bb): missing cluster in $Bitmap
Cluster accounting failed at 119740 (0x1d3bc): missing cluster in $Bitmap
Cluster accounting failed at 119741 (0x1d3bd): missing cluster in $Bitmap
Cluster accounting failed at 119742 (0x1d3be): missing cluster in $Bitmap
Cluster accounting failed at 119743 (0x1d3bf): missing cluster in $Bitmap
Cluster accounting failed at 119744 (0x1d3c0): missing cluster in $Bitmap
Cluster accounting failed at 119745 (0x1d3c1): missing cluster in $Bitmap
Cluster accounting failed at 119746 (0x1d3c2): missing cluster in $Bitmap
Cluster accounting failed at 119747 (0x1d3c3): missing cluster in $Bitmap
Cluster accounting failed at 119748 (0x1d3c4): missing cluster in $Bitmap
Cluster accounting failed at 119749 (0x1d3c5): missing cluster in $Bitmap
Cluster accounting failed at 119750 (0x1d3c6): missing cluster in $Bitmap
Cluster accounting failed at 119751 (0x1d3c7): missing cluster in $Bitmap
Cluster accounting failed at 119752 (0x1d3c8): missing cluster in $Bitmap
Cluster accounting failed at 119753 (0x1d3c9): missing cluster in $Bitmap
Cluster accounting failed at 119754 (0x1d3ca): missing cluster in $Bitmap
Cluster accounting failed at 119755 (0x1d3cb): missing cluster in $Bitmap
Cluster accounting failed at 3733978 (0x38f9da): missing cluster in $Bitmap
Cluster accounting failed at 3733979 (0x38f9db): missing cluster in $Bitmap
Cluster accounting failed at 3733980 (0x38f9dc): missing cluster in $Bitmap
Cluster accounting failed at 3733981 (0x38f9dd): missing cluster in $Bitmap
Cluster accounting failed at 3733982 (0x38f9de): missing cluster in $Bitmap
Cluster accounting failed at 3733983 (0x38f9df): missing cluster in $Bitmap
Cluster accounting failed at 3733984 (0x38f9e0): missing cluster in $Bitmap
Cluster accounting failed at 3733985 (0x38f9e1): missing cluster in $Bitmap
Cluster accounting failed at 3733986 (0x38f9e2): missing cluster in $Bitmap
Cluster accounting failed at 3733987 (0x38f9e3): missing cluster in $Bitmap
Cluster accounting failed at 3733988 (0x38f9e4): missing cluster in $Bitmap
Cluster accounting failed at 3733989 (0x38f9e5): missing cluster in $Bitmap
Cluster accounting failed at 3733990 (0x38f9e6): missing cluster in $Bitmap
Cluster accounting failed at 3733991 (0x38f9e7): missing cluster in $Bitmap
Cluster accounting failed at 3733992 (0x38f9e8): missing cluster in $Bitmap
Cluster accounting failed at 3733993 (0x38f9e9): missing cluster in $Bitmap
Cluster accounting failed at 3733994 (0x38f9ea): missing cluster in $Bitmap
Cluster accounting failed at 3733995 (0x38f9eb): missing cluster in $Bitmap
Cluster accounting failed at 3733996 (0x38f9ec): missing cluster in $Bitmap
Cluster accounting failed at 3733997 (0x38f9ed): missing cluster in $Bitmap
Cluster accounting failed at 3733998 (0x38f9ee): missing cluster in $Bitmap
Cluster accounting failed at 3733999 (0x38f9ef): missing cluster in $Bitmap
Cluster accounting failed at 3734000 (0x38f9f0): missing cluster in $Bitmap
Cluster accounting failed at 3734001 (0x38f9f1): missing cluster in $Bitmap
Cluster accounting failed at 3734002 (0x38f9f2): missing cluster in $Bitmap
Cluster accounting failed at 3734003 (0x38f9f3): missing cluster in $Bitmap
Cluster accounting failed at 3734004 (0x38f9f4): missing cluster in $Bitmap
Cluster accounting failed at 3734005 (0x38f9f5): missing cluster in $Bitmap
Cluster accounting failed at 3734006 (0x38f9f6): missing cluster in $Bitmap
Cluster accounting failed at 3734007 (0x38f9f7): missing cluster in $Bitmap
Cluster accounting failed at 3734008 (0x38f9f8): missing cluster in $Bitmap
Cluster accounting failed at 3734009 (0x38f9f9): missing cluster in $Bitmap
Cluster accounting failed at 3734010 (0x38f9fa): missing cluster in $Bitmap
Cluster accounting failed at 3734011 (0x38f9fb): missing cluster in $Bitmap
Cluster accounting failed at 3734012 (0x38f9fc): missing cluster in $Bitmap
Cluster accounting failed at 3734013 (0x38f9fd): missing cluster in $Bitmap
Cluster accounting failed at 3734014 (0x38f9fe): missing cluster in $Bitmap
Cluster accounting failed at 3734015 (0x38f9ff): missing cluster in $Bitmap
Cluster accounting failed at 3734016 (0x38fa00): missing cluster in $Bitmap
Cluster accounting failed at 3734017 (0x38fa01): missing cluster in $Bitmap
Cluster accounting failed at 3734018 (0x38fa02): missing cluster in $Bitmap
Cluster accounting failed at 3734019 (0x38fa03): missing cluster in $Bitmap
Cluster accounting failed at 3734020 (0x38fa04): missing cluster in $Bitmap
Cluster accounting failed at 3734021 (0x38fa05): missing cluster in $Bitmap
Cluster accounting failed at 3734022 (0x38fa06): missing cluster in $Bitmap
Cluster accounting failed at 3734023 (0x38fa07): missing cluster in $Bitmap
Cluster accounting failed at 3734024 (0x38fa08): missing cluster in $Bitmap
Cluster accounting failed at 3734025 (0x38fa09): missing cluster in $Bitmap
Cluster accounting failed at 3734026 (0x38fa0a): missing cluster in $Bitmap
Cluster accounting failed at 3734027 (0x38fa0b): missing cluster in $Bitmap
Cluster accounting failed at 3734028 (0x38fa0c): missing cluster in $Bitmap
Cluster accounting failed at 3734029 (0x38fa0d): missing cluster in $Bitmap
Cluster accounting failed at 3734030 (0x38fa0e): missing cluster in $Bitmap
Cluster accounting failed at 3734031 (0x38fa0f): missing cluster in $Bitmap
Cluster accounting failed at 3734032 (0x38fa10): missing cluster in $Bitmap
Cluster accounting failed at 3734033 (0x38fa11): missing cluster in $Bitmap
Cluster accounting failed at 3734034 (0x38fa12): missing cluster in $Bitmap
Cluster accounting failed at 3734035 (0x38fa13): missing cluster in $Bitmap
Cluster accounting failed at 3734036 (0x38fa14): missing cluster in $Bitmap
Cluster accounting failed at 3734037 (0x38fa15): missing cluster in $Bitmap
Cluster accounting failed at 3734038 (0x38fa16): missing cluster in $Bitmap
Cluster accounting failed at 3734039 (0x38fa17): missing cluster in $Bitmap
Cluster accounting failed at 3734040 (0x38fa18): missing cluster in $Bitmap
Cluster accounting failed at 3734041 (0x38fa19): missing cluster in $Bitmap
Cluster accounting failed at 3734042 (0x38fa1a): missing cluster in $Bitmap
Cluster accounting failed at 3734043 (0x38fa1b): missing cluster in $Bitmap
Cluster accounting failed at 3734044 (0x38fa1c): missing cluster in $Bitmap
Cluster accounting failed at 3734045 (0x38fa1d): missing cluster in $Bitmap
Cluster accounting failed at 3734046 (0x38fa1e): missing cluster in $Bitmap
Cluster accounting failed at 3734047 (0x38fa1f): missing cluster in $Bitmap
Cluster accounting failed at 3734048 (0x38fa20): missing cluster in $Bitmap
Cluster accounting failed at 3734049 (0x38fa21): missing cluster in $Bitmap
Cluster accounting failed at 3734050 (0x38fa22): missing cluster in $Bitmap
Cluster accounting failed at 3734051 (0x38fa23): missing cluster in $Bitmap
Cluster accounting failed at 3734052 (0x38fa24): missing cluster in $Bitmap
Cluster accounting failed at 3734053 (0x38fa25): missing cluster in $Bitmap
Cluster accounting failed at 3734054 (0x38fa26): missing cluster in $Bitmap
Cluster accounting failed at 3734055 (0x38fa27): missing cluster in $Bitmap
Cluster accounting failed at 3734056 (0x38fa28): missing cluster in $Bitmap
Cluster accounting failed at 3734057 (0x38fa29): missing cluster in $Bitmap
Cluster accounting failed at 3734058 (0x38fa2a): missing cluster in $Bitmap
Cluster accounting failed at 3734059 (0x38fa2b): missing cluster in $Bitmap
Cluster accounting failed at 3734060 (0x38fa2c): missing cluster in $Bitmap
Cluster accounting failed at 3734061 (0x38fa2d): missing cluster in $Bitmap
Cluster accounting failed at 3734062 (0x38fa2e): missing cluster in $Bitmap
Cluster accounting failed at 3734063 (0x38fa2f): missing cluster in $Bitmap
Cluster accounting failed at 3734064 (0x38fa30): missing cluster in $Bitmap
Cluster accounting failed at 3734065 (0x38fa31): missing cluster in $Bitmap
Cluster accounting failed at 3734066 (0x38fa32): missing cluster in $Bitmap
Cluster accounting failed at 3734067 (0x38fa33): missing cluster in $Bitmap
Cluster accounting failed at 3734068 (0x38fa34): missing cluster in $Bitmap
Cluster accounting failed at 3734069 (0x38fa35): missing cluster in $Bitmap
Cluster accounting failed at 3734070 (0x38fa36): missing cluster in $Bitmap
Cluster accounting failed at 3734071 (0x38fa37): missing cluster in $Bitmap
Cluster accounting failed at 3734072 (0x38fa38): missing cluster in $Bitmap
Cluster accounting failed at 3734073 (0x38fa39): missing cluster in $Bitmap
Cluster accounting failed at 3734074 (0x38fa3a): missing cluster in $Bitmap
Cluster accounting failed at 3734075 (0x38fa3b): missing cluster in $Bitmap
Cluster accounting failed at 3734076 (0x38fa3c): missing cluster in $Bitmap
Cluster accounting failed at 3734077 (0x38fa3d): missing cluster in $Bitmap
Cluster accounting failed at 3734078 (0x38fa3e): missing cluster in $Bitmap
Cluster accounting failed at 3734079 (0x38fa3f): missing cluster in $Bitmap
Cluster accounting failed at 3734080 (0x38fa40): missing cluster in $Bitmap
Cluster accounting failed at 3734081 (0x38fa41): missing cluster in $Bitmap
Cluster accounting failed at 3734082 (0x38fa42): missing cluster in $Bitmap
Cluster accounting failed at 3734083 (0x38fa43): missing cluster in $Bitmap
Cluster accounting failed at 3734084 (0x38fa44): missing cluster in $Bitmap
Cluster accounting failed at 3734085 (0x38fa45): missing cluster in $Bitmap
Cluster accounting failed at 3734086 (0x38fa46): missing cluster in $Bitmap
Cluster accounting failed at 3734087 (0x38fa47): missing cluster in $Bitmap
Cluster accounting failed at 3734088 (0x38fa48): missing cluster in $Bitmap
Cluster accounting failed at 3734089 (0x38fa49): missing cluster in $Bitmap
Cluster accounting failed at 3734090 (0x38fa4a): missing cluster in $Bitmap
Cluster accounting failed at 3734091 (0x38fa4b): missing cluster in $Bitmap
Cluster accounting failed at 3734092 (0x38fa4c): missing cluster in $Bitmap
Cluster accounting failed at 3734093 (0x38fa4d): missing cluster in $Bitmap
Cluster accounting failed at 3734094 (0x38fa4e): missing cluster in $Bitmap
Cluster accounting failed at 3734095 (0x38fa4f): missing cluster in $Bitmap
Cluster accounting failed at 3734096 (0x38fa50): missing cluster in $Bitmap
Cluster accounting failed at 3734097 (0x38fa51): missing cluster in $Bitmap
Cluster accounting failed at 3734098 (0x38fa52): missing cluster in $Bitmap
Cluster accounting failed at 3734099 (0x38fa53): missing cluster in $Bitmap
Cluster accounting failed at 3734100 (0x38fa54): missing cluster in $Bitmap
Cluster accounting failed at 3734101 (0x38fa55): missing cluster in $Bitmap
Cluster accounting failed at 3734102 (0x38fa56): missing cluster in $Bitmap
Cluster accounting failed at 3734103 (0x38fa57): missing cluster in $Bitmap
Cluster accounting failed at 3734104 (0x38fa58): missing cluster in $Bitmap
Cluster accounting failed at 3734105 (0x38fa59): missing cluster in $Bitmap
Cluster accounting failed at 3734106 (0x38fa5a): missing cluster in $Bitmap
Cluster accounting failed at 3734107 (0x38fa5b): missing cluster in $Bitmap
Cluster accounting failed at 3734108 (0x38fa5c): missing cluster in $Bitmap
Cluster accounting failed at 3734109 (0x38fa5d): missing cluster in $Bitmap
Cluster accounting failed at 3734110 (0x38fa5e): missing cluster in $Bitmap
Cluster accounting failed at 3734111 (0x38fa5f): missing cluster in $Bitmap
Cluster accounting failed at 3734112 (0x38fa60): missing cluster in $Bitmap
Cluster accounting failed at 3734113 (0x38fa61): missing cluster in $Bitmap
Cluster accounting failed at 3734114 (0x38fa62): missing cluster in $Bitmap
Cluster accounting failed at 3734115 (0x38fa63): missing cluster in $Bitmap
Cluster accounting failed at 3734116 (0x38fa64): missing cluster in $Bitmap
Cluster accounting failed at 3734117 (0x38fa65): missing cluster in $Bitmap
Cluster accounting failed at 3734118 (0x38fa66): missing cluster in $Bitmap
Cluster accounting failed at 3734119 (0x38fa67): missing cluster in $Bitmap
Cluster accounting failed at 3734120 (0x38fa68): missing cluster in $Bitmap
Cluster accounting failed at 3734121 (0x38fa69): missing cluster in $Bitmap
Cluster accounting failed at 3734122 (0x38fa6a): missing cluster in $Bitmap
Cluster accounting failed at 3734123 (0x38fa6b): missing cluster in $Bitmap
Cluster accounting failed at 3734124 (0x38fa6c): missing cluster in $Bitmap
Cluster accounting failed at 3734125 (0x38fa6d): missing cluster in $Bitmap
Cluster accounting failed at 3734126 (0x38fa6e): missing cluster in $Bitmap
Cluster accounting failed at 3734127 (0x38fa6f): missing cluster in $Bitmap
Cluster accounting failed at 3734128 (0x38fa70): missing cluster in $Bitmap
Cluster accounting failed at 3734129 (0x38fa71): missing cluster in $Bitmap
Cluster accounting failed at 3734130 (0x38fa72): missing cluster in $Bitmap
Cluster accounting failed at 3734131 (0x38fa73): missing cluster in $Bitmap
Cluster accounting failed at 3734132 (0x38fa74): missing cluster in $Bitmap
Cluster accounting failed at 3734133 (0x38fa75): missing cluster in $Bitmap
Cluster accounting failed at 3734134 (0x38fa76): missing cluster in $Bitmap
Cluster accounting failed at 3734135 (0x38fa77): missing cluster in $Bitmap
Cluster accounting failed at 3734136 (0x38fa78): missing cluster in $Bitmap
Cluster accounting failed at 3734137 (0x38fa79): missing cluster in $Bitmap
Cluster accounting failed at 3734138 (0x38fa7a): missing cluster in $Bitmap
Cluster accounting failed at 3734139 (0x38fa7b): missing cluster in $Bitmap
Cluster accounting failed at 3734140 (0x38fa7c): missing cluster in $Bitmap
Cluster accounting failed at 3734141 (0x38fa7d): missing cluster in $Bitmap
Cluster accounting failed at 3734142 (0x38fa7e): missing cluster in $Bitmap
Cluster accounting failed at 3734143 (0x38fa7f): missing cluster in $Bitmap
Cluster accounting failed at 3734144 (0x38fa80): missing cluster in $Bitmap
Cluster accounting failed at 3734145 (0x38fa81): missing cluster in $Bitmap
Cluster accounting failed at 3734146 (0x38fa82): missing cluster in $Bitmap
Cluster accounting failed at 3734147 (0x38fa83): missing cluster in $Bitmap
Cluster accounting failed at 3734148 (0x38fa84): missing cluster in $Bitmap
Cluster accounting failed at 3734149 (0x38fa85): missing cluster in $Bitmap
Cluster accounting failed at 3734150 (0x38fa86): missing cluster in $Bitmap
Cluster accounting failed at 3734151 (0x38fa87): missing cluster in $Bitmap
Cluster accounting failed at 3734152 (0x38fa88): missing cluster in $Bitmap
Cluster accounting failed at 3734153 (0x38fa89): missing cluster in $Bitmap
Cluster accounting failed at 13045575 (0xc70f47): missing cluster in $Bitmap
Cluster accounting failed at 13045576 (0xc70f48): missing cluster in $Bitmap
Cluster accounting failed at 13045577 (0xc70f49): missing cluster in $Bitmap
Cluster accounting failed at 13045578 (0xc70f4a): missing cluster in $Bitmap
Cluster accounting failed at 13045579 (0xc70f4b): missing cluster in $Bitmap
Cluster accounting failed at 13045580 (0xc70f4c): missing cluster in $Bitmap
Cluster accounting failed at 13045581 (0xc70f4d): missing cluster in $Bitmap
Cluster accounting failed at 13045582 (0xc70f4e): missing cluster in $Bitmap
Cluster accounting failed at 13045583 (0xc70f4f): missing cluster in $Bitmap
Cluster accounting failed at 13045584 (0xc70f50): missing cluster in $Bitmap
Cluster accounting failed at 13045585 (0xc70f51): missing cluster in $Bitmap
Cluster accounting failed at 13045586 (0xc70f52): missing cluster in $Bitmap
Cluster accounting failed at 13045587 (0xc70f53): missing cluster in $Bitmap
Cluster accounting failed at 13045588 (0xc70f54): missing cluster in $Bitmap
Cluster accounting failed at 13045589 (0xc70f55): missing cluster in $Bitmap
Cluster accounting failed at 13045590 (0xc70f56): missing cluster in $Bitmap
Cluster accounting failed at 13045591 (0xc70f57): missing cluster in $Bitmap
Filesystem check failed! Totally 224 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

========================================
```

GParted is telling me to do repairs from within Windows. I'm wondering if there's anything Linux can do to help. Is anyone aware of a free utility which can either help me fix these errors so I can get GRUB up and running again. Failing that, is there something which will at least let me get into the partition to recover some data before wiping it out and starting fresh?

Thanks for all your help!

---

### Post by stickmangumby on 2008-09-22
Under Linux, you could try running ntfsfix, which is part of the package ntfsprogs.

I'm yet to use Vista, but the XP install CD had an option to boot to a recovery console, or something like that. From there you could run useful commands like fixmbr and chkdsk.

Does Vista have something similar? If you boot to your install CD, does it detect your NTFS partition or your Windows installation?

Alternatively, you could try pulling out the drive and slaving it in another computer with Windows on it to try and fix the partition or recover files.

---

### Post by TeXtonyx on 2008-09-22
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
That shows how to install the Ubuntu driver which can mount and extract files from an NTFS partition. From Ubuntu one can manually mount the Windows partition.
mkdir /mnt/WinXP
mount -t ntfs /dev/sda1 /mnt/WinXP
That's from memory you might want to check the syntax. Then you cd /mnt/WinXP and
do an ls and see if the partition loaded. You should be able to burn a cd from Ubuntu to
backup your files. I think you will need bootrec for Vista to fix it. 
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by K0NY on 2008-09-22
Thank you for the suggestions.

> **stickmangumby said:**
> I'm yet to use Vista, but the XP install CD had an option to boot to a recovery console, or something like that. From there you could run useful commands like fixmbr and chkdsk.

Does Vista have something similar? If you boot to your install CD, does it detect your NTFS partition or your Windows installation?
Yes, I ran the Vista install disc which tried to recover the MBR and did a chkdsk. Neither was successful. I imagine since my MBR was using GRUB, Windows won't be much use.

> **TeXtonyx said:**
> [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
That shows how to install the Ubuntu driver which can mount and extract files from an NTFS partition. From Ubuntu one can manually mount the Windows partition.
mkdir /mnt/WinXP
mount -t ntfs /dev/sda1 /mnt/WinXP
Thanks those drivers look helpful. My problem is, the NTFS partition is damaged. So even Windows can't read it. Installing drivers for NTFS in Ubuntu probably won't do me much good (but I'll try it).

One of my techie friends pointed out that GRUB is a separate partition from NTFS. And since I don't see GRUB load up at all when the PC restarts, both it and the NTFS partition must be damages. So all I can really do is try to repair NTFS enough to recover my data from it before scrapping the whole thing and starting over.

---

### Post by timcredible on 2008-09-22
you want to use super grub disk (supergrubdisk.org) to repair the mbr when you have grub installed on it.  you can still run it and it might fix your mbr back to what it was.

---

### Post by charles_316 on 2008-09-22
i am currently experiencing a problem just like this except my GRUB does show up where I can choose to boot into Windows or Ubuntu..

however, everytime I try Windows normally or even safe mode, i get the blue screen of death and the computer restarts... 

when i try putting the windows CD in to repair or reinstall, it cannot even detect my hard drive....

this all happened after I installed Windows Service Pack 3 and then it took too long to shut down so i did a hard boot and that was a mistake lol

anyone have any advice?

---

### Post by K0NY on 2008-09-23
> **timcredible said:**
> you want to use super grub disk (supergrubdisk.org) to repair the mbr when you have grub installed on it.  you can still run it and it might fix your mbr back to what it was.

Thank you SO MUCH! Super Grub worked perfectly. I burned a boot CD with it and was back in the Windows install in no time. Once there, I ran a chkdsk /f and everything was fixed. My data is saved! Thanks again to everyone who helped.

> **charles_316 said:**
> i am currently experiencing a problem just like this except my GRUB does show up where I can choose to boot into Windows or Ubuntu..

however, everytime I try Windows normally or even safe mode, i get the blue screen of death and the computer restarts...
Your problem is actually completely different than mine from the symptops to the cause. It honestly sounds like something for the Microsoft forums though since it has nothing to do with Ubuntu.

---

