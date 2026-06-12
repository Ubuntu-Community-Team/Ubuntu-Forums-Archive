---
title: "Help with dd disk cloning"
date: 2008-09-19
forum: General Help
---

### Post by K.Morgan on 2008-09-19
I have been doing a bit of research on disk cloning in Ubuntu and have come to found from reading various user experiencing that dd is the best way to achieve this.  As it's in the command line i have found most of what's been written quite confusing and don't know where to start let alone how to actually achieve my clone.

I'm looking at cloning my original 80gb hard drive to a new 80gb hard drive and i want to do it using a Ubuntu live CD using dd.

Please could i get explanations in complete layman's terms as i'm fairly new to the command line stuff but want to learn.

thanks

---

### Post by Sycron on 2008-09-19
You may read the dd documentation. Type ```
man dd
``` to see the infos.

If you have a 120GB HDD you can't clone it on a 60GB HDD ...

---

### Post by Pelham123 on 2008-09-19
Have a look at this link:

[http://www.unix.com/filesystems-disks-memory/7243-use-dd-command.html](http://www.unix.com/filesystems-disks-memory/7243-use-dd-command.html)

Also be aware that if you intend to have both HDDs connected after the clone you will need to be careful of the UUIDs. UUIDs are partition identifiers, if you clone the disk you will also give your new partitions the same identifiers as the old disk...will totally confuse your OS.

---

### Post by K.Morgan on 2008-09-19
Thanks Sycron didn't realize that dd was already apart of Ubuntu.

Unfortunately the documentation does not help me and i'm still confused as to what i'm suppose to do.

---

### Post by K.Morgan on 2008-09-19
Thanks Pelham123 I'll read through that info now and report back.

---

### Post by K.Morgan on 2008-09-19
>  
The destination disk has to be identical to the source disk (including model
number and geometry).


Does this mean that both drives have to be exactly the same?

My destination disk is the same size as the original but is not from the same manufacturer, does this mean that dd will not work properly?

Also

Using the commands in that tutorial, will dd copy all the partition structures as well? as there are 3 partitions on the hard disk.

---

### Post by Jonie on 2008-09-19
Simple as that:

dd if=input_device of=output_device bs=16384 conv=notrunc //usually 32 sector blocks give the fastest speed

Larger block size stands for faster copying, then there is essential to use conv=notrunc, so that all data would be copied even if the input is not an exact multiple of the (large) blocks count

Yes it will work regardless of model, make and partitioning scheme. There is one condition: the new disk must not be smaller than the old one.

If the source disk is defective in some way, you might find ddrescue to be more useful in such case.

---

### Post by K.Morgan on 2008-09-19
Thanks Jonie.

Ddrescue might be something i would need to use actually, there are a few bad sectors to the source disk.

---

### Post by K.Morgan on 2008-09-20
Just been looking into ddrescue and i am very confused now, and from what i have read i doesn't look as if it does what i want it to which is to do an exact clone of the hard drive.

There are bad sectors on the hard drive so ddrescue is probably better used than just dd, but reading the information on ddrescue tells me that it makes an image of the hard disk and then I've got to mount that image and then take the information i want off that image and backup somewhere else?

All i want to do is an exact clone of my hard drive to a new hard drive of the same size, so when i put the new hard drive into my computer it boots up normally like the old hard drive did.

Please Help

---

### Post by Jonie on 2008-09-20
The ddrescue utility is mostly the same as dd, just uses a little bit different syntax than dd. It can be used with disk block devices as input and output. 

From:

[http://en.wikipedia.org/wiki/Dd_(Unix)]("http://en.wikipedia.org/wiki/Dd_(Unix)")

> GNU ddrescue can be used to copy data directly to a new disk if needed, just like Linux dd.

You may need to specify -d option to bypass kernel cache when reading damaged disk. Ddrescue won't truncate the output by default and will fill the gaps (uncopied bad sectors) with zeroes.

---

### Post by K.Morgan on 2008-09-20
Thanks Jonie, the -d option doesn't seem to exist in the help file, and when i run the command i get this error:

ddrescue: Cannot open output file.  Permission denied

Does the output disk need to be mounted first?  as i have left the output disk with no partitions at all just a blank 80gb, so it doesn't show up in Ubuntu to be able to mount it.

---

### Post by bingoUV on 2008-09-20
prefix the command with "sudo". It needs root privileges.

---

### Post by K.Morgan on 2008-09-20
Thanks bingoUV that did it.

---

### Post by Jonie on 2008-09-20
K.Morgan:

Don't copy by any means a mounted filesystem. The copy will be corrupted. Unmount it first.

---

### Post by nawab on 2010-03-21
Hello users, 

I have a UBUNTU server, recently i cloned the disk using dd and kept the second disk in box itself. yesterday i realized that because of UUID eatures it generated same UUID to my /dev/sdb partitions and it looks like it is using the mix of first disk and second disk. 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# /dev/sda5
UUID=be35a709-c787-4198-a903-d5fdc80ab2f8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

i have RedHat servers as well where i can easily do a dd and keep both disk in server. 
please let me know the workaround for this.

---

