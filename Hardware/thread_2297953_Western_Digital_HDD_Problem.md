---
title: "Western Digital HDD Problem"
date: 2015-10-07
forum: Hardware
---

### Post by arieleoar on 2015-10-07
Hi there!  Lastly i've got some problems with my Western Digital HDD, it stop sinning and continues in a 0,5second lapse when tries to write someting in a partition in particular. After that Then  it works normally with everything else that is running. (Desktop stucks for a while then every program runs without problem).  an output of dmesg in that moment:  ```
 ata3: lost interrupt (Status 0x50) [40085.024088] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen [40085.024094] ata3.00: failed command: WRITE DMA EXT [40085.024101] ata3.00: cmd 35/00:00:30:3f:24/00:04:1e:00:00/e0 tag 0 dma 524288 out [40085.024101]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout) [40085.024105] ata3.00: status: { DRDY } [40085.024119] ata3: soft resetting link [40085.204756] ata3.00: configured for UDMA/133 [40085.204767] ata3.00: device reported invalid CHS sector 0 [40085.204783] ata3: EH complete    
```  another:  ```
   [41790.016044] ata3: lost interrupt (Status 0x50) [41790.016075] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen [41790.016083] ata3.00: failed command: WRITE DMA EXT [41790.016095] ata3.00: cmd 35/00:30:28:6d:28/00:03:23:00:00/e0 tag 0 dma 417792 out [41790.016095]          res 40/00:00:00:4f:c2/40:00:1e:00:00/00 Emask 0x4 (timeout) [41790.016101] ata3.00: status: { DRDY } [41790.016116] ata3: soft resetting link [41790.197277] ata3.00: configured for UDMA/100 [41790.197288] ata3.00: device reported invalid CHS sector 0 [41790.197305] ata3: EH complete  
```  I don't post an output of the system because i've managed to reproduce this "halt" in Kubuntu Live CD, in OpenSUSE in a partition (sda2), and W#nXP in other partition(sda1).  The thing in common is that this error happens when i try to write or copy something in a third partition (sda3) without OS, but not everytime. The same happened when execute a game (FF8) that is located in that partition.  NOTE: There is a fourth partition (sda4) as SWAP  To me it looks like a corrupted sector, but i'm not sure, in Linux, there is some program that fixes or relocates bad sectors? or a minimal howto?  Thanks! Saludos!

---

### Post by tgalati4 on 2015-10-08
Run *badblocks* on the problematic partition.  Could be a mechanical issue with the drive head, or simply the disk is wearing out.

```
sudo badblocks /dev/sda3
```

If you get more than a few dozen bad sectors, then it's time to retire the disk drive.

---

### Post by arieleoar on 2015-10-08
Hi again! Thanks @tgalati4!

I've run codeblocks in that partition and to be exact it'd found 28 bad sectors, too bad :( . But i can't plan a "retirement" for the HDD, i don't have a cent today...

So next, i need to fix/patch this. I've run fsck on that partition, but it don't fixes it, and doesn't seem to do anything (neither revise the filesystem), here an output:

```

fsck from util-linux 2.21.2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.

```

I know that fsck only works with the filesystems, but in "man codeblocks" it makes a reference to use fsck, an e2fsck (that works only with ext* partitions). The partition in cuestion /dev/sda3 is an NTFS partition.

So, there is a program (in preference for linux) that relocates or mark that sectors as bad, for NTFS partiton? i ask this because the last time i've to use a program like that was a long time ago and under DOS...

Thanks again! Saludos!

NOTE: Is possible that this bad sectors R/W errors makes the drive stops and start spinning as i've described in the first post?

---

### Post by tgalati4 on 2015-10-08
The disk drive's firmware will automatically move bad sectors to "reserve sectors".  It will attempt to read a bad sector hundreds of times and if there are 10 sectors to read to retrieve a file, then it could take several minutes to get that file.  When you run out of "reserve sectors" then you really lose data.  With 28 bad sectors, we really don't know how many bad sectors have already been relocated.

I don't use Windows so I can't say what tool is used to repair NTFS, other than chkdsk.

Back up your important data to USB sticks.  Your hard disk could fail completely without notice.

---

### Post by arieleoar on 2015-10-08
Thanks for the fast reply!

i've realized something: checking the setup inside the tower (is a desktop pc), i've found the problem, or a part that maybe causes it...
For everyone who are reading this _Don't ever connect a HDD in the same power supply cable-pack with an DVD/CD drive: The DVD/CD drive will draw the power (current intensity ~ Ampere) of the HDD when both are in demand of read/write, specially if the power supply is less than 500W._

Each cable-pack of power supply comes generally with two plugs, so i'll recommend use one cable-pack for only connect the HDD and the other to each DVD/CD drive, in my case now i've reconnected one to HDD drive and the other to an DVD Drive and a CD Drive.

I'll mark this as solved, because there is nothing more to do with this HDD, thanks to @tgalati4.

Saludos!

---

### Post by tgalati4 on 2015-10-09
That is a good catch.  Although all the power cables generally come from the same power rails of a power supply, it's possible that you have a worn-out solder connection on a single power cable--something that is easily fixed if you know your way around a power supply.  I had a hard disk act in a similar fashion on an old linux server--the power connector had become loose on the back of the drive.  Needed some tie straps to secure the wires to prevent vibration from backing out the power connector in the future.

---

