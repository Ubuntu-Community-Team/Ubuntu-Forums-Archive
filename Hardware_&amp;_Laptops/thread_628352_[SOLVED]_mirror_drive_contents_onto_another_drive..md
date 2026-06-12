---
title: "[SOLVED] mirror drive contents onto another drive..."
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by buccaneere on 2007-12-01
My HP DV 9xxx nr has two HDD's. Can I copy the entire contents, Ubuntu, settings, **everything**, etc, onto the secondary drive, with both in the machine?

Thanks.....

---

### Post by buccaneere on 2007-12-01
> **buccaneere said:**
> My HP DV 9xxx nr has two HDD's. Can I copy the entire contents, Ubuntu, settings, **everything**, etc, onto the secondary drive, with both in the machine?

Thanks.....

bumpintodatop..........

---

### Post by matt91 on 2007-12-01
i just tar the filesystem to backup with a cronjob, the command i use is like:

```
tar -czf /backup/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup --exclude=/mnt --exclude=/sys /
```

RSYNC is also worth looking at.

---

### Post by buccaneere on 2007-12-01
> **matt91 said:**
> i just tar the filesystem to backup with a cronjob, the command i use is like:

```
tar -czf /backup/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup --exclude=/mnt --exclude=/sys /
```

RSYNC is also worth looking at.

Thanks Matt...

I'm guessin the first command is an internal OS/linux execution (as opposed to a function of a downloaded program?)?

...and RSYNC IS a program I would need to download???

---

### Post by buccaneere on 2007-12-02
> **buccaneere said:**
> Thanks Matt...

Originally Posted by matt91  
i just tar the filesystem to backup with a cronjob, the command i use is like:


[HTML]Code:
tar -czf /backup/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup --exclude=/mnt --exclude=/sys /

RSYNC is also worth looking at.[/HTML]
I'm guessin the first command is an internal OS/linux execution (as opposed to a function of a downloaded program?)?

...and RSYNC IS a program I would need to download???

bumpintodatop...

---

### Post by tgalati4 on 2007-12-02
Log into rescue mode.

# cp /dev/sda /dev/sdb

This copies then entire device (sda) to another device (sdb).  Partitions and everything copy over.

Edit your grub to point to sdb and boot and check around to make sure everything is in place.

This also works if the second drive is not partitioned/formatted.  If partitioned, the partitions need to be the same size (or larger) and you can copy partition-by-partition.

#cp /dev/sda1 /dev/sdb1
#cp /dev/sda2 /dev/sdb2
#cp /dev/sda3 /dev/sdb3

Make sure you understand the the device/partition numbering scheme on your system.  If you screw up, you will lose data.

---

### Post by buccaneere on 2007-12-03
> **tgalati4 said:**
> Log into rescue mode.

# cp /dev/sda /dev/sdb

This copies then entire device (sda) to another device (sdb).  Partitions and everything copy over.

Edit your grub to point to sdb and boot and check around to make sure everything is in place.

This also works if the second drive is not partitioned/formatted.  If partitioned, the partitions need to be the same size (or larger) and you can copy partition-by-partition.

#cp /dev/sda1 /dev/sdb1
#cp /dev/sda2 /dev/sdb2
#cp /dev/sda3 /dev/sdb3

Make sure you understand the the device/partition numbering scheme on your system.  If you screw up, you will lose data.

Excellent! Thanks................

---

### Post by buccaneere on 2007-12-06
> **tgalati4 said:**
> Log into rescue mode.

# cp /dev/sda /dev/sdb

This copies then entire device (sda) to another device (sdb).  Partitions and everything copy over.

Edit your grub to point to sdb and boot and check around to make sure everything is in place.

This also works if the second drive is not partitioned/formatted.  If partitioned, the partitions need to be the same size (or larger) and you can copy partition-by-partition.

#cp /dev/sda1 /dev/sdb1
#cp /dev/sda2 /dev/sdb2
#cp /dev/sda3 /dev/sdb3

Make sure you understand the the device/partition numbering scheme on your system.  If you screw up, you will lose data.

Rescue mode? Edit grub? Exactly what is that?

Okay... I brought up command line as root user, then entered

[HTML]cp /dev/sda /dev/sdb[/HTML]

How long does this take? After two minutes, I have no 'return' yet.

Was I supposed to put **#** at the beginning of the code line? What should be the 'return'? A progress indicator of some sort?

Thanks!

---

### Post by buccaneere on 2007-12-07
> **tgalati4 said:**
> Log into rescue mode.

# cp /dev/sda /dev/sdb

This copies then entire device (sda) to another device (sdb).  Partitions and everything copy over.

Edit your grub to point to sdb and boot and check around to make sure everything is in place.

This also works if the second drive is not partitioned/formatted.  If partitioned, the partitions need to be the same size (or larger) and you can copy partition-by-partition.

#cp /dev/sda1 /dev/sdb1
#cp /dev/sda2 /dev/sdb2
#cp /dev/sda3 /dev/sdb3

Make sure you understand the the device/partition numbering scheme on your system.  If you screw up, you will lose data.

WORKED LIKE A CHARM! 

WITH CONVOLUTION. SEE THIS:
[http://ubuntuforums.org/showthread.php?p=3906750#post3906750](http://ubuntuforums.org/showthread.php?p=3906750#post3906750)
UNDERSTAND IT, AND YOU'RE TRULY A GENIUS!

What's that stuff about rescue mode, and editing GRUB tho'???

---

### Post by komputes on 2008-02-20
> This also works if the second drive is not partitioned/formatted.

Works for me as long as I create the partitions on the drive have been created. if I simply do "sudo cp /dev/sda1 /dev/sdb1", then a new file called sdb1 is created and then truncated. I simply created the partitions using gparted before using your instructions. Then again I was not in rescue mode when doing it. I will try in rescue mode and post my findings.

---

