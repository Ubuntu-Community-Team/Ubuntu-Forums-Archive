---
title: "hard drive not being found"
date: 2009-12-18
forum: Hardware
---

### Post by lunaparadox on 2009-12-18
I added a 3rd drive to my system to use for storage. but ubuntu doesn't see the drive as being attached. The drive shows up in bios and in windows. I even formatted it in windows to see if that may help with no luck.

sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: ST380011A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 8.16
       serial: 3JVBHRMQ
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b2ddb2dd
  *-disk:1
       description: ATA Disk
       product: WDC WD3200AAJB-0
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAV20570411
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00047247
  *-cdrom
       description: CD-R/CD-RW writer
       product: CD-RW SOHR-5238S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 4S03
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
 this is what ubuntu sees.
and from 
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
240 heads, 63 sectors/track, 10333 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb2ddb2dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10332    78109888+   7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047247

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       22388   179829688+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           22388       26212    30716280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           33479       38913    43656637+   5  Extended
/dev/sdb4           26213       33478    58364145   83  Linux
/dev/sdb5           33479       33600      975208+  82  Linux swap / Solaris
/dev/sdb6           33601       38913    42676168+  83  Linux

Partition table entries are not in disk order
 I'm at a loss any help would be appreciated.
Oh and I installed kubuntu to another partition as well to see if a new install would find the drive.

---

### Post by lunaparadox on 2009-12-18
Tried booting to live cd with same results. So I disconnected the sda and sdb drives and made sdc to sda and booted to live cd and then ubuntu saw it but putting everything back to normal it's gone again. Anybody??

---

### Post by lunaparadox on 2009-12-18
Well alot more testing and no further. I put other drives in that spot and some worked and some didn't. Using a live cd. I even put this drive in that spot and it wouldn't show up. Put a dieing drive in there and it had no problem finding it lol. I'm thoroughly confused at this point. oh and windows can see everything I put in there which is the part that really has me scratching my head. Well this has been my evening and I guess no one else has the answer so I guess I just give up for now and hope that something comes to me.

---

### Post by teward on 2009-12-19
you're problem might not be that its not being found, rather its not auto-mounting.

---

### Post by lunaparadox on 2009-12-19
sudo mount /dev/sdc1
mount: special device /dev/sdc1 does not exist

---

### Post by Grenage on 2009-12-19
If it's not being seen at all in Ubuntu, I'd be suspect of cable/port.  Windows is a lot more forgiving when it comes to flaky hardware (most people don't see that as a good thing).

---

### Post by moddie666 on 2009-12-19
Hi.

Are you still using IDE Drives? If so are the Jumper settings on the drives correct (i.e. master/slave/cable select)?

Please tell me how the hardware is arranged meaning:
Who is master/slave on IDE Channel 1 and 2?
If you are using Cableselect try using master/slave.

Sidenote:
If it is not in fdisk -l or lshw Linux doesnt know its there.

greetings
/moddie

ps:
Just saw it, Grenage is following the same trail of thought I did.

---

### Post by lunaparadox on 2009-12-19
Yes it's ide and I have changed the pins to master and slave and back to cable select. I have even changed the the cables went through about 12 different cables with no luck. I was thinking the drive or cable were bad.
but as I said I tried other drives and some can be found and some can't. I just removed a drive from there that has been there for over a 3 years. started getting smart warnings so was trying to add anew drive but it seems that only the western digital drives I have are being seen, but seagate and maxtor drives on that port are not.
  It is in the slave position on the second ide port with a cdr as master.
thought it might be the ide port as well but I'm not real sure how they work and would think that the master on that port would fail as well. but I can remove the cdr and put the drive as master then it shows up.
   maybe it's just a problem with certain drives and that port IDK.

---

### Post by Grenage on 2009-12-19
Based on your troubleshooting, I would guess that it is indeed the port.  It's also possible/likely that the original drive is fine, and that smart was picking up on the port problem.

---

### Post by lunaparadox on 2009-12-19
I would agree but would that not also mean that the device what ever it be that was on the end portion of the cable would have the same fate? it is ide port 2 with 2 devices on it one device works fine but the one doesn't doesn't seem right but maybe I am no expert when it comes to IDE ports and their internal workings but that is what I am searching for now. lol not that it will change weather the port is dead or not I just want to know now.

---

### Post by Grenage on 2009-12-19
With two devices on the same port, I would have expected both to have problems.  You've already changed the cable, so I can only assume that the port is flaky but not completely dead.

---

### Post by Anthony Littlejohn on 2009-12-19
I had a simular problem in wich ubuntu recongnize the drive as scsi verse sata that could be a possible problem also there for you would have to download the drivers for that drive and install them by using a usb floppy drive if you do not have a floppy drive on your computer. You will need to choose the option for adding a 3rd party devise then it will ask you to load the devise driver.hope this helps.

---

### Post by lunaparadox on 2009-12-19
Thanks for your help like I said I am searching for the magical grail of how those ports work now. just wonder why I can put the one drive back in and it still works that's the most confusing part. I can put it in and it's found every time. and when I reinstall it the smart warning goes away which makes me agree there is maybe nothing wrong with the drive. and why it sees some drives and not others my head hurts ouch!

---

### Post by lunaparadox on 2009-12-19
seems others with this ide interface have had similar issues since kernel 2.6.28. :( I was using 8.04 of ubuntu until recently I did a clean install of 9.10 I hate to go backwards but that may be the solution for now. I have a extra partition for testing so I will be installing 8.04 on there and see what happens.

---

### Post by lunaparadox on 2009-12-19
Well my 8.04 disc was messed up so I used an old pclinuxos disk and
this is what I have found
fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
240 heads, 63 sectors/track, 10333 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10332    78109888+   7  HPFS/NTFS

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       22388   179829688+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2           22388       26212    30716280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hdb3           33479       38913    43656637+   5  Extended
/dev/hdb4           26213       33478    58364145   83  Linux
/dev/hdb5           33479       33600      975208+  82  Linux swap / Solaris
/dev/hdb6           33601       38913    42676168+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdd: 80.0 GB, 80000000000 bytes
240 heads, 63 sectors/track, 10333 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       10333    78117448+   7  HPFS/NTFS

As you can see Disk /dev/hdd: 80.0 GB, 80000000000 bytes
240 heads, 63 sectors/track, 10333 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

the disk is found with an older kernel so I guess this would be a bug in the latest kernels.

---

### Post by lunaparadox on 2009-12-19
The IDE interface is this
description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
just so everyone knows.

---

