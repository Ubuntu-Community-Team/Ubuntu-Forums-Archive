---
title: "WD 1TB drive poor performance"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by Goobie81 on 2008-04-20
So i have this new system i put together and it's performing miserably in the IO department . 

It's a Gigabyte EP35-DS3P, Q6600 running Gutsy
I've got 4 WD 1TB drives in a RAID5 array, and dm-crypt sits on that (/data filesystem - not used by host or Vmware systems)
(sdc-sdf)

I've got 2x 320 GB PATA drives in RAID1 which form the Os and the VMware filesystem (/vms) 
(sda, sdb)

PATA drive:
```

root@phantom:/proc# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   5680 MB in  2.00 seconds = 2841.67 MB/sec
 Timing buffered disk reads:  114 MB in  3.04 seconds =  37.52 MB/sec

```

SATA drive:
```

root@phantom:/proc# hdparm -Tt /dev/sdd

/dev/sdd:
 Timing cached reads:   7350 MB in  2.00 seconds = 3677.83 MB/sec
 Timing buffered disk reads:  204 MB in  3.02 seconds =  67.61 MB/sec

```

When ever the system comes under any amount of load (from Vm's or initiated by the host), the IO wait just shoots up the queues start filling up

kernel is 2.6.22.9 (manual compile - I have attached the config file used. Needed to enable HPET_EMULATE_RTC to fix a vmware clock problem) 

smart drive details :
```

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EACS-00ZJB0
Firmware Version: 01.01B01
User Capacity:    1,000,204,886,016 bytes
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated

```

md1 (RAID1 PATA drives)
```

root@phantom:~# hdparm -Tt /dev/md1

/dev/md1:
 Timing cached reads:   6090 MB in  2.00 seconds = 3046.88 MB/sec
 Timing buffered disk reads:  178 MB in  3.03 seconds =  58.80 MB/sec

```

md2 (RAID5 SATA drives)
```

root@phantom:~# hdparm -Tt /dev/md2

/dev/md2:
 Timing cached reads:   6380 MB in  2.00 seconds = 3191.88 MB/sec
 Timing buffered disk reads:  196 MB in  3.01 seconds =  65.05 MB/sec


```

fjgaude  posted his hdparm performance of his array consisting of new-ish drives ([here]("http://ubuntuforums.org/showthread.php?t=744901")):
```

/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec

```

I don't have much experience with these emerging desktop technologies so i can't do much troubleshooting.

---

### Post by sdennie on 2008-04-20
Actually, I think 65MB/s is pretty reasonable for a single SATA2 drive.  You'll notice in the 212MB/s he is referencing md32 which is a RAID array so, those number are probably from a 4 disk RAID0.

---

### Post by Goobie81 on 2008-04-20
Sorry :) i should have done preview instead of post :)

i was still editing the page to put the MD performance results

<snip> put into main post

---

### Post by sdennie on 2008-04-20
What is the output of cat /proc/mdstat?  Are one of the disks in the RAID5 offline or rebuilding?

---

### Post by Goobie81 on 2008-04-20
Googling around suggests that the drive speed is about right. Still this system is struggling to cope with demand it should be able to eat for breakfast

nah they are all sync'd up
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sde1[0] sdf1[3] sdc1[2] sdd1[1]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid1 sda3[0] sdb3[1]
      293137984 blocks [2/2] [UU]
      
md0 : active raid1 sda2[0] sdb2[1]
      19326080 blocks [2/2] [UU]

---

### Post by sdennie on 2008-04-20
The single drive speed seems correct but, I don't understand why the RAID5 array would perform at about the same level as a single disk.  I don't think the speed will scale linearly but, it should be a noticeable speedup.

---

### Post by keld on 2008-05-11
There is something on performance on [http://linux-raid.osdl.org/index.php/Performance](http://linux-raid.osdl.org/index.php/Performance) - you should be able to get something like 240 MB/s out of your 4 disks in a raid10,f2 array.

---

### Post by kylemallory on 2008-06-21
I am experiencing similar type results, from a similar setup (using the same drives in a 4-disk, RAID 0).  Based on googling around, and other posts on UbuntuForums, it appears there is some issue with these specific drives (WD10EACS [1TB Caviar Green]) in particular.

In my case, I have two RAID's.  #1 is a 1.36TB software RAID5 (6x250GB WD Drives), hosted on a 3ware 9500 12-channel controller.  #2 is a 3.6TB 4-disk hardware RAID0 (4x1TB WD), hosted on the same 3ware 9500 12-channel controller.

I may come back and reconfigure the 2nd raid as for software to get a better comparison, but generally speaking, I should be getting similar performance, if not faster from the 4TB RAID0.

/dev/md0 is RAID #1.

hdparm -Tt /dev/md0
/dev/md0:
 Timing cached reads:   1766 MB in  2.00 seconds = 882.85 MB/sec
 Timing buffered disk reads:  1034 MB in  3.00 seconds = 344.51 MB/sec

/dev/sdh1 is RAID #2.

hdparm -Tt /dev/sdh1
/dev/sdh1:
 Timing cached reads:   1806 MB in  2.00 seconds = 902.74 MB/sec
 Timing buffered disk reads:  434 MB in  3.01 seconds = 144.17 MB/sec


Cached reads are what they are.
Buffered reads, however, is a dramatic difference, with the software RAID5 more than 2x faster.


My guess is that this has something to do with the "Green" drives variable RPM speed.  I have nothing to base this one, its just a hunch.  That perhaps, the linux drivers are doing something that is preventing the drive from spinning up to 7200rpms (and staying at 5400rpms).

---

### Post by kylemallory on 2008-07-14
Just a quick update on this.  I broke my hardware RAID0 and configured the 4 WD10EAC drives as a JOBD array, and got the same dismal 11MB/s read performance from individuals drives.

My motherboard has an 8 channel Adaptec SAS controller on-board.  I moved the 4 WD10EAC drives from the 3ware controller to the Adaptec.  I configured the drives as a JOBD again, and this time, my data performance is hovering in around ~62MB/s.  I have yet to configure the drives in a software RAID, but I'm expecting appropriate performance numbers.

My best guess at this point... The Adaptec SAS is SATA II compatible, while the 3ware is not.  The WD drives have a jumper to force the drive to SATA 1.0, but these have not been set, relying on the drive to auto-negotiate down.  So, I suspect there is some known issue with SATA/SATA 2 compatibility/performance.  If someone is curious, I may moves the drives back to the 3ware controller and set the jumpers, however, there is no point in me continuing for my own personal needs, since I'll always get better performance from SATA 2, on the Adaptec controller anyway, not to mention that the Adaptec runs on the bus at 100MHz, while the 3ware is only 66MHz.  Asside from the 12 channels, there isn't much point in it (fortunately, my 6x250GB drive array is SATA 1.0), except for maybe moving a small amount of the processing off onto the already slow RISC processor on the 3ware card.

---

