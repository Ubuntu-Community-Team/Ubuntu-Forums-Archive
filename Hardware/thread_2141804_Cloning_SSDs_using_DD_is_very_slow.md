---
title: "Cloning SSDs using DD is very slow"
date: 2013-05-03
forum: Hardware
---

### Post by ninocass on 2013-05-03
Hi All

I am clonning a backup of my SSD to an identical drive.  Im using DD running from a live ubuntu install on a USB drive.  Both SSDs are OCZ Vertex 2 (285MB/s read - 275MB/s write)  Both are connected via SATA however DD is reporting 16.5MB/s any ideas?

Many Thanks

---

### Post by 64bitiso on 2013-05-03
CloneZilla! Do it :)

---

### Post by ibjsb4 on 2013-05-03
As I use clonezilla too, so Im no expert, but did find this.

[http://ubuntuforums.org/showthread.php?t=2050603](http://ubuntuforums.org/showthread.php?t=2050603)

---

### Post by matt_symes on 2013-05-03
Hi

What's the exact dd command you are using ?

Kind regards

---

### Post by ahallubuntu on 2013-05-03
~

---

### Post by ninocass on 2013-05-04
Ive tried clonezilla with little speed gains over DD.

As an extra piece of info, the source disk is full disk encrypted and the second disk is loaded into the optical bay using a sata HDD adapter ([Linky]("http://www.tomshardware.co.uk/ssd-laptop-upgrade-optical-bay,review-32366.html"))

Ive tried experimenting with the bs argument on DD it starts quickly initially then drops to ~16MB/s, the full command is something like

```
dd if=/dev/sda of=/dev/sdc bs=1m
```

To test I mounted a network share and DD wrote to that across the network at a consistant 80MB/s (share is running on a normal 2TB HDD).  Reading back from the share to the second disk dropped to 16MB/s so it seems that the issue lies with the writing of the second drive.  Would the optical drive have a lower bandwidth? surely sata is standard.

Perhaps one of these is the way to go, especially for weekly backups.

[http://www.amazon.co.uk/Icy-Box-IB-120CL-U3-Docking-Function/dp/B006CS1VN4](http://www.amazon.co.uk/Icy-Box-IB-120CL-U3-Docking-Function/dp/B006CS1VN4)

---

### Post by matt_symes on 2013-05-04
Hi

> To test I mounted a network share and DD wrote to that across the  network at a consistant 80MB/s (share is running on a normal 2TB HDD).   Reading back from the share to the second disk dropped to 16MB/s so it  seems that the issue lies with the writing of the second drive.  Would  the optical drive have a lower bandwidth? surely sata is standard.

That is quite telling; the write speed to the optical caddy.

Have you ran any speed and timing tests to the optical caddy using hdparm ?

I forget the exact syntax but it's something like this...

```
sudo hdparm -tT /dev/sdX
```

...where sdX is the caddied drive.

This will give you read speeds. 

Write speed are usually found using dd though and that is where you have the problem.

I would suggest taking the drive out the caddy and run some speed test on it and see what you get. It'll implicate/eliminate the caddy.

Kind regards

---

### Post by ninocass on 2013-05-07
Sorry for the delay in posting back, I've just got around to doing some comparisons.

I have 4 SSDs in total, 


2 X OCZ Vertex 2
2 X Kingston Tech - SSD Now V Series 


the OCZ sits in the HDD bay and the Kingston in the optical bay.

The drives are soley used for backups and I am only able to test write speeds on 1 of each as it will destroy the data.

I tested each drive in each module bay and the results are pretty consistant.


```
-----------------------------------------------------
***OCZ Vertex***
-----------------------------------------------------
*HARDDRIVE BAY*
-----------------------------------------------------
_READ_
/dev/sda:
 Timing cached reads:   11748 MB in  2.00 seconds = 5878.46 MB/sec
 Timing buffered disk reads: 506 MB in  3.01 seconds =[COLOR=#FF0000] **168.13 MB/sec**[/COLOR]
_WRITE_
dd count=1k bs=1M if=/dev/zero of=/dev/sdc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 4.09531 s,[COLOR=#FF0000] **262 MB/s**[/COLOR]
-----------------------------------------------------
*OPTICAL BAY*
-----------------------------------------------------
_READ_
/dev/sda:
 Timing cached reads:   14752 MB in  2.00 seconds = 7383.34 MB/sec
 Timing buffered disk reads: 512 MB in  3.01 seconds = [COLOR=#FF0000]**170.09 MB/sec**[/COLOR]
_WRITE_
dd count=1k bs=1M if=/dev/zero of=/dev/sdc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 4.19666 s,[COLOR=#FF0000]** 256 MB/s**[/COLOR]

-----------------------------------------------------
=====================================================
***Kingston Technology - SSDNow V-Series***
-----------------------------------------------------
*HARDDRIVE BAY*
-----------------------------------------------------
_READ_
/dev/sda:
 Timing cached reads:   14806 MB in  2.00 seconds = 7410.71 MB/sec
 Timing buffered disk reads: 708 MB in  3.00 seconds =[COLOR=#FF0000]** 235.79 MB/sec**[/COLOR]
_WRITE_
dd count=1k bs=1M if=/dev/zero of=/dev/sda
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 5.88576 s, [COLOR=#FF0000]**182 MB/s**[/COLOR]
-----------------------------------------------------
*OPTICAL BAY*
-----------------------------------------------------
_READ_
/dev/sdc:
 Timing cached reads:   14064 MB in  2.00 seconds = 7038.79 MB/sec
 Timing buffered disk reads: 708 MB in  3.00 seconds =[COLOR=#FF0000]** 235.96 MB/sec**[/COLOR]
_WRITE_
dd count=1k bs=1M if=/dev/zero of=/dev/sdc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 5.59555 s,[COLOR=#FF0000]** 192 MB/s**[/COLOR]
-----------------------------------------------------

```

I just cloned the Kingstons with no issues:

```

 dd  bs=1M if=/dev/sdc of=/dev/sdd
64023257088 bytes (64 GB) copied, 327.13 s, **[COLOR=#FF0000]196 MB/s[/COLOR]**

```

The OCZ is another matter:

```

dd  bs=1M if=/dev/sdc of=/dev/sdd
246+0 records in
246+0 records out
257949696 bytes (258 MB) copied, 3.45116 s,** [COLOR="#FF0000"][COLOR="#FF0000"]74.7 MB/s[/COLOR][/COLOR]**
585+0 records in
585+0 records out
613416960 bytes (613 MB) copied, 13.5509 s,**[COLOR="#FF0000"] 45.3 MB/s[/COLOR]**
901+0 records in
901+0 records out
944766976 bytes (945 MB) copied, 23.5395 s, **[COLOR="#FF0000"]40.1 MB/s[/COLOR]**
1175+0 records in
1175+0 records out
1232076800 bytes (1.2 GB) copied, 33.5549 s, **[COLOR="#FF0000"]36.7 MB/s[/COLOR]**
^C1188+0 records in
1188+0 records out
1245708288 bytes (1.2 GB) copied, 35.348 s, **[COLOR="#FF0000"]35.2 MB/s[/COLOR]**

```

On plugging both drives in and comparing dmesg one drive has the following error:
```

[ 2818.023196] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2818.247166] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 2818.257910] ata1.00: ATA-8: OCZ-VERTEX2, 1.35, max UDMA/133
[ 2818.257922] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[ 2818.320239] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 2818.331050] ata1.00: configured for UDMA/133

```

---

### Post by matt_symes on 2013-05-07
Hi

Try adding this to your kernel command line.

```
libata.noacpi=1
```

After grepping the kernel source, i could not see it actually being used anywhere in kernel 3.8. 

```
matthew-S206:/home/matthew/storage/linux_source/linux-3.8/drivers/ata % grep -r "libata_noacpi" ../../*
../../drivers/ata/libata-core.c:int libata_noacpi = 0;
../../drivers/ata/libata-core.c:module_param_named(noacpi, libata_noacpi, int, 0444);
../../drivers/ata/libata.h:extern int libata_noacpi;
Binary file ../../drivers/ata/libata.ko matches
Binary file ../../drivers/ata/libata.o matches
Binary file ../../drivers/ata/libata-core.o matches
matthew-S206:/home/matthew/storage/linux_source/linux-3.8/drivers/ata % 
```

This is the vanilla kernel source with the liquorix patch through and it's still listed in kernel-parameters.txt so it maybe worth a try.

It'll be interesting to see if it has any effect and if it affects the other drives.

Kind regards

---

### Post by ninocass on 2013-05-08
Adding  ```
libata.noacpi=1
``` worked a treat!

The average clone speed was around 100MB/s!!

Thank you for the help

---

### Post by matt_symes on 2013-05-08
Hi

> **ninocass said:**
> Adding  ```
libata.noacpi=1
``` worked a treat!

The average clone speed was around 100MB/s!!

Thank you for the help

Excellent ! I'm glad it's working.

I'll have to check why my cursory grep did not reveal more as well. Something else to add to the list :D

I'll mark this thread as solved for you.

Kind regards

---

