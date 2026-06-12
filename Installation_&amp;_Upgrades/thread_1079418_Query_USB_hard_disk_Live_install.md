---
title: "Query USB hard disk Live install"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by HarshReality on 2009-02-24
OK, I rebuilt a live CD with all the current bells and whistles (codecs etc.) and figured this would be a perfect drive-by OS. Only thing missing is space.. in rolls WD Passport 500G USB 2.0 drive 'woohoo'. 

Issue. Cant create USB install with the drive as its reading as a HDD even though its on the USB.

So anybody havea solution for how I could install the live CD onto a USB hard disk?

* No its powered via USB so no external power.

---

### Post by cariboo on 2009-02-24
When you boot from your LiveCD does te drive show up in System-->Administration-->Partition Editor? 

It will show as a hard drive even if it is connected via usb the device label should be something like

```
/dev/sdb1
```

I would also suggest getting a powered usb hub and plug the power cable into that instead of the computer.

Jim

---

### Post by HarshReality on 2009-02-24
> **cariboo907 said:**
> When you boot from your LiveCD does te drive show up in System-->Administration-->Partition Editor? 

It will show as a hard drive even if it is connected via usb the device label should be something like

```
/dev/sdb1
```

I would also suggest getting a powered usb hub and plug the power cable into that instead of the computer.

Jim

Yep shows as /dev/sde under /media/disk

---

### Post by HarshReality on 2009-02-24
Under your suggestion I tried alternate ports on the machine as well as a powered hub and the same result.. the system mounts it but it just wont see it as a 'USB' drive.

id:	
disk
description: 	SCSI Disk
product: 	5000BEV External
vendor: 	WD
physical id: 	
0.0.0
bus info: 	
scsi@7:0.0.0
logical name: 	
/dev/sde
version: 	1.75
serial: 	WD-WXNX08SWC317
size: 	465GiB (500GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	4
signature	=	4ad9c6f3

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1731](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1731)

---

### Post by HarshReality on 2009-02-25
Is OK, I got it anyway (great thing about linux.. you bang on it enough and it works out 99% of the time!).

I used an online tutorial and created a custom ISO with Skype, codecs, unrar etc. and all updates to the 23rd.

Used this tutorial:
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)

So, Ive shaved a gig off the top (MY ISO was only 811M) created a 4G casper-rw file and formatted the rest as fat32 (Yea I know the filesize limit but Im not backing up DVD ISOs.

So now my end result is a current portable ISO on a pocket drive that actually holds enough space to be able to move something from a dead system if I need to WITHOUT (and this was the big one for me) having to lug a power pack around.

---

