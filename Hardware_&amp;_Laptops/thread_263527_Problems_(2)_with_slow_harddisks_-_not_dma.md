---
title: "Problems (2) with slow harddisks - not dma"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by zaphodb on 2006-09-23
Hello everybody, 

my computer gives me a headache because of performance problems with my disks. Maybe somebody can give me a hint to solve one of these two problems: 

(1) I have a Raid1 array (md1) from two partitions on two 200GB ATA disks for my /home, which is too slow; bonnie++ says:


[FONT="Fixedsys"]```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
marvin           2G 13035  33  7130   3  4800   2  9657  25 15041   4 206.5   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 18876  97 +++++ +++ 15550  99 18906  99 +++++ +++  3895  26

```[/FONT]

Both 200GB disks contain three partitions: 1GB swap, 15GB for a RAID0 array for /, and 180GB for Raid1 for /home. 
The disks are connected to a Highpoint 302 ATA card. 

The Raid0 for / (md0) on the same controller, same disks is not so slow; bonnie++ says: 

[FONT="Fixedsys"]```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
marvin           2G 36174  92 56782  25 24291  10 31405  82 64319  15 351.0   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 20457  98 +++++ +++ 17119  99 20274  99 +++++ +++ 16153  99
```[/FONT]

Now, I thought a Raid1 should be about as fast as a single hard disk!? If I look at my 160GB disk on hda, I get: 

[FONT="Fixedsys"]```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
marvin           2G 37444  94 38104  18 18122   7 26802  63 52727  12 230.1   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 20152 100 +++++ +++ 16022  99 14052  72 +++++ +++ 15076  99
```[/FONT]

That's much faster! I have checked hdparm, latency, everything should be ok, as far as I can see. 
So, what could I do to make that Raid1 faster?

(2) while looking for the problem, I found another one even worse. My tv recordings directory is a single 120GB harddisk, hdc1 on the second port of the nforce2 chipset ide controller (together with a dvd-rw as hdd). Reading from that disk is ok, but writing to it is very slow! If I copy files from hda, md0 or md1 to hdc1, I get only very low throughput.  I have tried copying a 4.9GB file from the recording directory to the other drives and back; the times are 


hdc -> null 2:03
hdc -> md0  2:11
hdc -> md1  4:19 (! - see complaint (1))
hdc -> hda  2:30

md0 -> null 0:52
md0 -> hdc  6:47 (!!!)
md0 -> hda  2:23

md1 -> null 2:09
md1 -> hdc  6:41 (!!!)
md1 -> hda  2:54
hda -> hdc  6:43 (!!!)

hdc1 was formatted as xfs; I tried emptying it, then reformatting as ext3, reiserfs... always the same result. 

I booted into windows from hda, reformatted hdc1 as ntfs and copied the same file from c: to d: and it took only about 1:53 minutes!!! (No time command for exact measurement)

All the reported tests in linux were done in single user mode; when repeating it in the normal runlevel 2, the numbers are slightly different but basically say the same. I have also tried with/without "noapic", it's the same.

I have compiled a new kernel without SMP, the same.  

My setup: Athlon XP2500+ on MSI nforce2 motherboard; 1GB Ram, HPT302 IDE (non-raid) controller card; Ubuntu 6.06.1.
hdparm on all four disks is like hdc (geometries differ): 
/dev/hdc:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

and udma6 for hda, hdc and udma5 for hde, hdh.

hda: hda1 (winXP), hda2 (/boot), hda3 (linux rescue), hda4 (/mp3)
hdc: hdc1 (/tv)
hde=hdh: hde1 (swap), hde2 (Raid0 mdm for /), hde3 (Raid1 mdm for /home)

Other PCI cards: Symbios SCSI, DVB-T, DVB-S, USB2.0 card. 
Video: Matrox P650 AGP with matrox driver. 

Any ideas? I am at the end of my possibilities... 

Thanks!

---

### Post by zaphodb on 2006-09-24
-deleted-

---

