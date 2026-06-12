---
title: "Re-appropriating a partition"
date: 2008-10-08
forum: Hardware
---

### Post by ysr23 on 2008-10-08
Hi there,

I have recently built a mythtv box on a machine with a 60gb drive, as this got bigger I sought to increase the capacity so using [this guide]("http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/") I successfully cloned the drive onto a 125gb drive.

I say successfully but mythweb still reports me having the old drive:
```
Total Disk Space:

    * Total Space: 55,978 MB
    * Space Used: 50,837 MB
    * Space Free: 5,141 MB

```

this doesn't look right - i did change that drive, so i SSH in (i am remote at the minute) and **df -h** giving me

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   47G  5.1G  91% /
varrun                379M  116K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   76K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   39M  340M  11% /lib/modules/2.6.24-19-generic/volatile
```

So i am now very conrfused - i did physically change the drive and the western digital sticker said 125gb - so i try **$ sudo lshw -C disk**from the CL

 ```
 *-disk
       description: ATA Disk
       product: Maxtor 6Y120L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y40QQMZE
       size: 114GiB (122GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=90909090
```

Now, i remember a CL tool for viewing the disk partitions but for the life of me cannot remember but i assume that i only have a 60gb Ubuntu partition and the rest is given over to DOS on this new drive. 

So is there a way i can extend my ubuntu partition into this DOS area - i'm not interested on what might be on it currently. 


many thanks in advance

---

### Post by pytheas22 on 2008-10-08
The way that hard drive manufacturers usually calculate disk capacity exaggerates the real space on their drive--they will consider 1 megabyte == 1000 kilobytes, instead of 1024 kilobytes like the rest of the world.  On top of that, space is lost to file-system overhead.  So although your drive said that it was 125 GB, it may be the case that only 114 are really available.

Does that answer your question, or only part of it?

gparted has a CLI frontend called just 'parted', so that might help you, although it still doesn't approach the convenience and clarity of the gparted graphical interface.

---

### Post by ysr23 on 2008-10-08
> **pytheas22 said:**
> The way that hard drive manufacturers usually calculate disk capacity exaggerates the real space on their drive--they will consider 1 megabyte == 1000 kilobytes, instead of 1024 kilobytes like the rest of the world.  On top of that, space is lost to file-system overhead.  So although your drive said that it was 125 GB, it may be the case that only 114 are really available.
oh, no sorry i maybe wasn't making myself clear, i realise that there is discrepency between reported by system and manufacturers - but my first HD was 60gb, i was running out of space so i cloned this onto a new HD, the 125gb one, but under ubuntu and mythtv it is reporting that i only have 60gb - so i am missing about 55gb or thereabouts somewhere - now when i **$ sudo lshw -C disk** it tells me that:
```
     size: 114GiB (122GB)
       capabilities: partitioned partitioned:dos

```
so i am guessing that perhaps my missing GB is a hd partition? i may be wrong though, either way i want it re-appropriated into my ubuntu area if possible

> **pytheas22 said:**
> 
gparted has a CLI frontend called just 'parted', so that might help you, although it still doesn't approach the convenience and clarity of the gparted graphical interface.

thanks, but usually maintenance to my mythbox is done remotely from ssh so if its possible i would prefer to do it from CL if possible

---

### Post by pytheas22 on 2008-10-08
> thanks, but usually maintenance to my mythbox is done remotely from ssh so if its possible i would prefer to do it from CL if possible

'parted' can be run from the command line.  Just type 'sudo parted' and follow the instructions on the screen.

You could also forward X over ssh by connecting with the -X argument (provided you have an X server of some kind running on the remote machine):
```

ssh -X username@mythbox-machine
```

Once logged in, type:
```

sudo gparted
```

and graphical gparted should start on your remote display.

I think at this point that your best bet is to use parted or gparted to figure out what's going on with your partitions.

Also, 'testdisk' can tell you the partition structure of your disks, so you may want to install that ('sudo apt-get install testdisk') and run it ('sudo testdisk').

---

### Post by ysr23 on 2008-10-08
> **pytheas22 said:**
> 'parted' can be run from the command line.  Just type 'sudo parted' and follow the instructions on the screen.

Many thanks,

this tells me:
```
partition 1 is 121GB, but the file system is 59.2GB
```

so this is kind of what i already know, what i need to do here is try to extend this to take up the 'missing' area if possible

---

### Post by lswb on 2008-10-08
gparted or the command line program parted can be used to "grow" the cloned 60GB partition into the total available on the new disk. This cannot be done to a mounted partition, and you can't unmount the boot partition, so you will need to boot with a live CD or gparted CD. You may be able to get a ssh server running from a live CD, or you can temporarily attach a keyboard & monitor.

---

### Post by pytheas22 on 2008-10-08
As the poster above says, I think that your best option is probably to attach a monitor to the machine, boot to a live CD, and use gparted there to make the changes.  Another equally viable option is to move the hard drive to another computer and edit it there.

Also, you should of course be backing up any important data on the hard disk if you're going to edit the partition table, which always carries a risk.

---

### Post by ysr23 on 2008-10-08
many thanks to both of you - ok, i have booted from live cd and started gparted, but here i'm lost - this reports the drive as bein 113gb with 7gb free - now this may very well be true but nowhere does it give me any info about partitions?

Why, when booted into my system does it report that i only have 59gb, but live cd reports 113gb?

---

### Post by pytheas22 on 2008-10-08
Did you look at it using the graphical version of gparted from your Ubuntu system (i.e. not from the live CD)?  Does it still report different information there?

Also, if you select View>Device Information in parted, it will tell you how many sectors are on your hard drive in all.  You can also right-click on each partition (in your case it sounds like there's only one partition) and select "Information" to find out how many sectors that partition occupies.  Does all the math add up?

---

### Post by ysr23 on 2008-10-09
Hi - yes, its the same in both, and yes it does appear to be only one partition:

Model:  ATA Maxtor 
Size:   113.00 GiB
Used:   105.52 GiB  (93%)
Unused: 7.47 GiB    (7%)

Path:   /dev/sda1
Status: Not mounted

First Sector: 63
Last Sector: 236974814
Total Sectors: 236974752

---

### Post by pytheas22 on 2008-10-09
If you mount the drive, does gparted also think it's only 59 GB?  Or does it continue to say that it's 114?

---

