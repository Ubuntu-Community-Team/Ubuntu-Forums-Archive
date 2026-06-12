---
title: "2nd hard drive appears in bios but not file browser"
date: 2011-02-17
forum: Hardware
---

### Post by carpentermikep on 2011-02-17
oracle@Oracle:~$ sudo fdisk -l
[sudo] password for oracle: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32a732a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7079    56862036   83  Linux
/dev/sda2            7080        9614    20362387+  83  Linux
/dev/sda3            9615        9726      899640    5  Extended
/dev/sda5            9615        9726      899608+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32f032ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS




oracle@Oracle:~$ dmesg | grep ata
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] Memory: 499640k/523708k available (4685k kernel code, 23116k reserved, 2125k data, 660k init, 0k highmem)
[    0.000000]       .data : 0xc05936e7 - 0xc07a6e88   (2125 kB)
[    0.290592] libata version 3.00 loaded.
[    0.435666] ata_piix 0000:00:1f.1: version 2.13
[    0.435739] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.440773] scsi0 : ata_piix
[    0.484535] scsi1 : ata_piix
[    0.484589] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.484594] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.681239] ata2.00: ATAPI: LITEON  DVD-ROM LTD163, GDHF, max UDMA/33
[    0.681292] ata2.01: ATAPI: SAMSUNG CD-R/RW SW-240B, BD11, max UDMA/33
[    0.689415] ata2.00: configured for UDMA/33
[    0.705314] ata2.01: configured for UDMA/33
[    4.260415] ata1.00: ATA-6: WDC WD800BB-75JHA0, 05.01C05, max UDMA/100
[    4.260420] ata1.00: 156250000 sectors, multi 8: LBA 
[    4.261534] ata1.01: ATA-5: WDC WD400BB-00CLB0, 05.04E05, max UDMA/100
[    4.261539] ata1.01: 78165360 sectors, multi 8: LBA 
[    4.268317] ata1.00: configured for UDMA/100
[    4.285242] ata1.01: configured for UDMA/100
[    4.332393] Write protecting the kernel read-only data: 1844k
[    5.139932] REISERFS (device sda1): using ordered data mode
[   57.512328] EXT3-fs: mounted filesystem with ordered data mode.


Hi I have a 80 gig hard drive with ubuntu 10 installed on a 60 gig partition.  I have the other 20 gigs blank.  I just installed a 40 gig hard drive and it shows up in BIOS but I cannot get the gui desktop to recognize it.  

I want to do a fresh install on the 40 gig hardrive, then repartition the 80 as my data drive.  

Pretty green... so be easy on me.  Thanks.

---

### Post by trundlenut on 2011-02-17
What shows up in the Disk Utility? Do you have the option to mount it? (System->Administration->Disk Utility)

From what you have posted above the second drive is formatted with a single NTFS partition, so Ubuntu is recognising it.

---

### Post by carpentermikep on 2011-02-17
Sweet.  Its the simple things... Disk Utility... who woulda thunk?

Ok... so now I have a 80 gig drive and a 40 gig drive.  And they both show up and the 40 gig is now formatted, file system checked, and mounted.

40 GB partitioned to ext4

and

80 GB in 4 partitions:

58 GB in reiserfs
21 GB in ext3
Extended 921 MB
921 MB Swap Space

I wasn't the one who set up this machine.   Why would it have these 4 partitions?  Is it a good idea to leave it alone?

There is nothing in my 21 GB partition.  I was thinking it would be wise to have ubuntu reinstalled fresh on the 40 gig and then use the 80 gig for all my data.

I'm not sure how to make that happen though, my "home folder" has 36.3 GB of data; it is in the 58 GB partition along with the ubuntu OS files.  There is 12.9 GB of free space in that partition.

Thoughts?

carpentermikep

---

### Post by trundlenut on 2011-02-17
the extended partition just holds the swap partition.  No idea why you have the ext3 partition, you could always delete it and expand the reiserfs partition to fill the space.

If you do start again I would put the root partition and swap on the smaller disc and the home on the larger disk.

---

### Post by carpentermikep on 2011-02-17
> **trundlenut said:**
> the extended partition just holds the swap partition.  No idea why you have the ext3 partition, you could always delete it and expand the reiserfs partition to fill the space.

If you do start again I would put the root partition and swap on the smaller disc and the home on the larger disk.

Ok... so if I do as you say... delete the ext3 partition... then expand the reiserfs partition.  How do I safely remove the installation on that partition to allow more space?  and how could I upgrade that partition to ext4?  Call me crazy but I kind of find reiserfs creepy with the whole murdered wife thing.

---

### Post by carpentermikep on 2011-02-17
Ok... does this sound like a fair protocol:

1) Do a fresh install on the new 40 gig drive.

2) Reboot onto the fresh install on the 40 gig drive.

3) Delete everything except the home folder on the 58 gig partition of the 80 gig drive.

4) Edit the partitions on the 80 gig drive so it is 40gigs reiserfs and 40 gigs ext4.

5) Move the home folder over to the ext4 side; put any excess onto my 16 GB usb flash.

6) Delete the reiserfs partition and the swap file partition.

7) Expand the 40gig ext4 partition to fill the 80 gig drive.


that's intimidating, especially #4

Aside from the 16 GB usb flash, I also have a separate machine with a fresh install of ubuntu 10 on a 40 gig HD (with no personal data) as a resource.

carpentermikep

---

### Post by trundlenut on 2011-02-17
1. Backup the data you want to keep.
2. Boot from a live CD.
3. Erase everything on both discs using gparted.
4. Choose install from live cd and choose the manual (or advanced) option when you get to the disc partioning and set the 80gb drive as a single ext4 partition mounted as /home then partition the smaller disc with most of the drive as an ext4 partition mounted as / and a smaller swap partition twice the size of your systems memory.

---

### Post by carpentermikep on 2011-02-17
> **trundlenut said:**
> 1. Backup the data you want to keep.
2. Boot from a live CD.
3. Erase everything on both discs using gparted.
4. Choose install from live cd and choose the manual (or advanced) option when you get to the disc partioning and set the 80gb drive as a single ext4 partition mounted as /home then partition the smaller disc with most of the drive as an ext4 partition mounted as / and a smaller swap partition twice the size of your systems memory.


That does sound a lot easier.  Thanks...  

One more thing.  Does the swap partition need to be exactly twice?  What if I intend to upgrade my RAM soon, should I just oversize now or is that bad for some reason?

---

### Post by trundlenut on 2011-02-17
> **carpentermikep said:**
> That does sound a lot easier.  Thanks...  

One more thing.  Does the swap partition need to be exactly twice?  What if I intend to upgrade my RAM soon, should I just oversize now or is that bad for some reason?

Currently my main machine has about the same size swap as ram because I upgraded the ram after I had installed ubuntu.  I have never used more than about 20% of swap at any point.

How much ram do you have now and what might you upgrade it to?

---

### Post by quadproc on 2011-02-17
> **carpentermikep said:**
> 
One more thing.  Does the swap partition need to be exactly twice?  What if I intend to upgrade my RAM soon, should I just oversize now or is that bad for some reason?
The swap should be at least as large as the amount of RAM that you plan to have.  The reason for this is that the system stores its RAM contents in the swap area when you use the hibernate function.

quadproc

---

### Post by trundlenut on 2011-02-17
> **quadproc said:**
> The swap should be at least as large as the amount of RAM that you plan to have.  The reason for this is that the system stores its RAM contents in the swap area when you use the hibernate function.

quadproc

Good point!

---

### Post by carpentermikep on 2011-02-17
Both machines I'm using now were curb finds that had corrupted windows, otherwise physically functional 2.4ghz 40gig machines with 512 MB.  I salvaged my 80 gig data drive from my machine that got struck by lightening and had a friend boot the first machine up with ubuntu on that 80 gig drive.   I did the second one myself with its 40 gig drive.. and then that left me with one more 40 that you just helped me get back online.  One of curb finds was filled with cheesy porn... the other was full of personal data including account #'s and passwords.  Morons; "shift-delete", format....

Anyway.  I think I'll just leave 2 gigs free on each machine for swap room.  I didn't think to do it when I set up the 40 gig machine, can I go back and do it now?

Thanks again.

carpentermikep

---

