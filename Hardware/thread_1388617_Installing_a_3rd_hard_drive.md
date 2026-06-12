---
title: "Installing a 3rd hard drive"
date: 2010-01-23
forum: Hardware
---

### Post by rapattack1 on 2010-01-23
Hi I have just mounted the secondary hard drive after a new install of Ubuntu 9.10 a couple of weeks ago but now am trying to install a 3rd drive. They are all sata drives and the third one is a 2.5" instead of the usual 3.5. I have never done this before but thought it was possible as there is a sata connection for the drive. When connected the machine will not boot. I get the post screen and the bios shows the drive is there but no further. I just get the cursor blinking at the top of a black screen and the only way out is the turn off the power switch on the front of the puter. It is a 2nd hand drive so ultimately i do not know if it is working so any suggestions for me to know if this drive is viable would be handy.
```

sudo lshw -C disk
*-cdrom:0               
       description: DVD writer
       product: DVD-RW DVR-108DX
       vendor: PIODATA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.10
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD reader
       product: DVD SOHD-16P9S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: FS07
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: ST380013AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 8.12
       serial: 5MR1FPLQ
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00002f97
  *-disk:1
       description: ATA Disk
       product: WDC WD360GD-00FL
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 31.0
       serial: WD-WMAKH1066528
       size: 34GiB (37GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c5e7c

``` 

The drive i am trying to put in is a Seagate Momentus 5400.3 160gb.

This is a new scenario for me so I am not sure what to do next!

---

### Post by hemimaniac on 2010-01-23
well i know there is pysdm, and gparted. Gparted will allow you to create/manipulate partitions in any disk
and pydsm is a graphical storage manager ( available from the repos ) with pysdm you can set the drive to mount via defaults and it will auto create the fstab entry, or you can edit the settings in pysdm and it will auto modify the fstab entries.

---

### Post by ttoilleb on 2010-01-23
I am not sure about this, but looking over the info, I believe that POST is attempting to boot from your new drive.

Why you may ask?

*-disk:0
  bus info: scsi@2:0.0.0

*-disk:1
  bus info: scsi@3:0.0.0

When you plugged in the new drive, it probably was assigned - scsi@_**1**_:0.0.0 - which would make it the First device on the bus.

The solution, 
Turn the PC off.
1. Move the sata cable from the WD drive to the new Seagate drive
2. Move the sata cable from the existing Seagate drive to the WD drive
3. Plug the remaining cable into the existing Seagate drive.

---

### Post by rapattack1 on 2010-01-23
No the new drive is not plugged in when i posted the info. I am not able to boot remember when I have that drive plugged in.
The existing seagate drive is the master drive with Ubuntu on it and it is on the first sata connection on the MB and the WD drive is on the 2nd connection on the MB. I had put the new drive on the first raid(disabled in the bios as raid) connection on the MB.
I am not sure about the numbering thing that you mention. This machine is a bit advanced for me. The whole sata thing is confusing, Because there are no ide hard drives in this machine the ide master cable is clear so the hard drives are listed in the bios after the cd drives. I forgot the names ...maybe third master and third slave?

So I won't be able to boot into Ubuntu if I have the drives plugged the way you suggest!

---

### Post by ttoilleb on 2010-01-24
Ah, missing information.  What MB to you have?  How did you disable the raid?

With the current info, I still think you need to move some cables.
IE: without the new drive, it works.  With the new drive plugged in, it doesn't work.  Given that post starts and then a blank screen, that indicates to me that post is going to the new drive to boot,

Is there anything in your bios to set boot drive sequence?

---

### Post by rapattack1 on 2010-01-24
My MB is a P4P800-E Asus. I disabled the raid in the bios. I have used this computer for ages without raid as someone told me how to do it ages ago.

Yeah I agree that things look the way you say but how could it book with the mbr is on the primary drive which is the Seagate one.

Yep i have the boot sequence set probably the dvd writer first(not sure), then the seagate drive(existing), then the floppy. I don't know what it is when the newer 160gb drive is plugged in as now that i think about it i can't get into the bios at that time. I tried many times. I replugged and unplugged and no change. I also unplugged, did a boot into Ubuntu, shut down, replugged and tried with the 160gb and not able to get into bios or anything. 

What i might try tomorrow when i have time to pull the box out again is try the 160gb drive on it's own. Maybe that will tell me something and then try the cables the way you said....
thanks for persisting with me!!!!

---

### Post by IcarusR on 2010-01-24
> new drive on the first raid(disabled in the bios as raid) connection

Surely if you have it connected to a sata raid port & have disabled raid in the bios then that port will not work at all.

---

### Post by rapattack1 on 2010-01-24
Ah I don't understand the whole raid thing much but my understanding is that raid is the setup where two drives work as one and they mirror each others data so there is a copy of what is on the first drive if anything goes wrong. I was toldf to disable this ages ago as certain things weren't working that i can't remember now. I have had drives connected to 3 sata connections on the board since then and only just recently took 1 off because it was faulty. It was the original WDC drive that was on the 2nd spot . It was 37gb or whatever the other WDC drive is that i have on the 2nd spot now. The 80gb seagate drive is from another machine that i just put in ....anyway now this is getting me confused and i better get back to other things.
It was working fine as it prior to this new arrangements drives.

---

