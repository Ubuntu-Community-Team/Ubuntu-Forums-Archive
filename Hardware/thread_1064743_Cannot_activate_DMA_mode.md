---
title: "Cannot activate DMA mode"
date: 2009-02-09
forum: Hardware
---

### Post by su1c1de on 2009-02-09
Hi

I recently build myself a new fileserver with 12 hard disks. additionally to the ide and sata controller on the mainboard i installed a promise ide controller and a dawicontrol sata controller which are all working fine.
only the ide controller on the mainboard is giving me a hard time. it is not activating dma mode, so my system hard disk and my dvd writer are runnign very slow.

sudo hdparm -t /dev/hda gives me

```
Timing buffered disk reads:    6 MB in  4.04 seconds =   1.48 MB/sec
```

this is pretty much annoying since i wanted to run multiple vms from that disk and from time to time burn some dvds on that dvd-writer which is connected on the same channel.

if i try  sudo hdparm -d1 /dev/hda, i get:

```
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)
```

i googled for some time and had found some solutions which are not working for me. like blacklisting modules and activating modules. finally i found a solution which helped me for some time: i started the kernel with the "hda=noprobe" option. but after some time and a blackout it stopped working and i do not know why

i think this has something to do with the drivers that are used by that ide controller. And i cannot figure out how to change them. another cause of the problem might be that i have to use lilo to boot the system. this is also the reason why my ide drive is named hda instead of sda. grub could not handle all the diffrent controllers and drives. it was unable to find the boot partition. 
it seems that lilo forces the drive to be hda while the system wants it to be sda. for example is the root filesytem mounted as sda although it is hda

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             148G   19G  122G  14% /
varrun                2.0G  2.5M  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  152K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/sda1             233G   63G  171G  27% /media/music
/dev/sdb1             233G   35G  199G  15% /media/recordings
/dev/hda6             126G  5.7G  114G   5% /media/stuff
/dev/sdg1             190G   12G  179G   7% /media/sda1
/dev/sdh1             149G   77G   73G  52% /media/sdb1
/dev/sdi1             298G  256G   43G  86% /media/sdc1
/dev/sdj1             190G  181G  9.9G  95% /media/sdd1
/dev/md0              2.8T  1.1T  1.8T  37% /media/md0
/dev/sdl1             298G  203G   96G  68% /media/backup
/dev/sdk1             466G  354G  112G  76% /media/private
```

i have no idea what to do next... i have already tried to use a sata disk as system disk, but with ubuntu having changing the order of the drives with each boot grub cannot boot correctly at all and it seems lilo cannot address the correct sata disk with the root filesystem and pass it to the kernel. 
So i am stuck with the ide hard disk. is there a way to set the driver for the ide controller manually?

i am running hardy 64bit server

---

### Post by johnzollo on 2009-10-23
If hda=noprobe worked, maybe the kernel was updated -- hda=noprobe became obsolete after 2.6.25 (Intrepid Ibex).  If you want to troubleshoot the problem you probably want to look at libata.  That's the module that handles ide in Ubuntu.  Anything involving ide_core or hda, hdb, etc. won't work.

Good luck!  

Ask for help if you need it.  Maybe someone will know!

See you around!:guitar:

Sincerely,
john

---

### Post by su1c1de on 2009-10-23
hey

eventually i figured out how to install grub correctly. since then the drive has been running fine with dma. it seems lilo messed something up

thanks anyway

---

### Post by johnzollo on 2009-10-23
you're welcome!

(Although I didn't do much :) )

-john

---

