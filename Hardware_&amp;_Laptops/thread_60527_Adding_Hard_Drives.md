---
title: "Adding Hard Drives"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by zoqaeski on 2005-08-28
Earlier on tonight I added a second hard drive to this machine, and now I have a question: How do I format it and get it going and made useable? I can't find anything, and GNOME-help keeps on crashing  :mad: 

cheers
Robbie

---

### Post by pmjdebruijn on 2005-08-28
Hi,

Well depends, on which IDE channel did you add the harddrive? The device names are generally like this:

Primary Master  /dev/hda
Primary Slave  /dev/hdb
Secondary Master  /dev/hdc
Secondary Slave  /dev/hdd

You can also try 'dmesg | less' (in the Terminal), to see what device name your new harddrive has gotten.

**Please beware, any of the following command are destructive, and may destroy your data, if you get the device name wrong!**

You can partition the disc by typing this: 'cfdisk /dev/hdd', substitute your drive for hdd.

Then you can create a filesystem on the drive by typing this: 'mkfs -t ext3 /dev/hdd1'

Then you can add the new drive to your '/etc/fstab' to have it mounted automatically at every boot.

Regards,
Pascal de Bruijn

---

### Post by zoqaeski on 2005-08-28
[QUOTE=pmjdebruijn]You can partition the disc by typing this: 'cfdisk /dev/hdd', substitute your drive for hdd.[/QUOTE]
No problems, that worked.
> Then you can create a filesystem on the drive by typing this: 'mkfs -t ext3 /dev/hdd1'
Done that, no problems.
> Then you can add the new drive to your '/etc/fstab' to have it mounted automatically at every boot.
This one's got me - I used sudo gedit /etc/fstab and added the drive (I think I did, anyway) but I've got no idea if it has been mounted or not at all. Some help here please?

cheers
Robbie

---

### Post by blackant on 2005-08-28
How about adding a SCSI hdd?

---

### Post by pmjdebruijn on 2005-08-28
[QUOTE=blackant]How about adding a SCSI hdd?[/QUOTE]

SCSI hdd's are called (for example) /dev/sda... etc...

---

### Post by pmjdebruijn on 2005-08-28
Okay,

The /etc/fstab file is only used at boot, or when you execute the mount command.

So you need to reboot to mount your new drive, or type:
```
sudo mount /mnt/mynewdrive
```
Substitute /mnt/mynewdrive for the mountpoint you chose.

Anyway, if you paste your /etc/fstab in here, I can take a look at it...

Regards,
Pascal de Bruijn

---

### Post by blackant on 2005-08-28
[QUOTE=pmjdebruijn]SCSI hdd's are called (for example) /dev/sda... etc...[/QUOTE]
ok. Thanks for the fast reply. ;)

---

### Post by zoqaeski on 2005-08-28
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda3       /usr            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /               ext3    defaults        0       0
``` 
Thats the fstab - maybe all of the hard drives need to be in the same location :?

Robbie

---

### Post by pmjdebruijn on 2005-08-28
Hi,

Please take a look at your own fstab. Something there seriously doesn't make sense...

You are using the same mount point (/) twice. You need to mount it somewhere else. For example 'mkdir /mnt/data', and use that.

Filesystems can't be mounted on top of each other! To create one huge drive out of two of more drives you can use RAID or LVM, but that's another topic all together!

Regards,
Pascal de Bruijn

---

### Post by zoqaeski on 2005-08-29
Cool, it all works now! Thanks! I had to make a folder in the drive, fix up a few things, but now it works.
I have one remaining question, however:
How would this slave drive cope if I had to reinstall the OS on the primary drive? Would it still work?

cheers
Robbie

---

### Post by pmjdebruijn on 2005-08-29
Make a folder in the drive? Huh?

**WARNING:** Do you use the drive with the fstab you supplied! This may cause data-loss in the future!!!

Anyway, why wouldn't it cope with a reinstall... just don't reformat the partition (double check)...

Regards,
Pascal de Bruijn

---

### Post by zoqaeski on 2005-08-30
I modified the fstab to look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda3       /usr            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /media/hdd ext3 defaults,auto,uid=1000,gid=1000 0 0
```

Is there something wrong with it?

Robbie

---

### Post by pmjdebruijn on 2005-09-02
Nope, that's just fine. I misunderstood. Sorry.

Regards,
Pascal de Bruijn

---

### Post by dbrine on 2005-09-04
Here is the best guide I could find. 


[http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4232/1/)

---

