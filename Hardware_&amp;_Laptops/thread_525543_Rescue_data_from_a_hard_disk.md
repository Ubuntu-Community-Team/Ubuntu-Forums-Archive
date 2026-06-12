---
title: "Rescue data from a hard disk"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by boondocks on 2007-08-14
I have a Ubuntu 6.06.1 Server system running smoothly on /dev/hda

Just connected a second hard disk.  It shows up under /dev/hdb
I would like to rescue the data off this second disk.
Fdisk says that the partition on hdb is 8e Linux LVM

How do I mount this LVM partition?

---

### Post by moore.bryan on 2007-08-14
*i'm not sure about lvm partitions, but you could try ```
sudo mount /dev/hdb# /mnt/hdb
``` where # is the number of the partition you're trying to mount...*

---

### Post by boondocks on 2007-08-14
I tried that.
mount says that I need to specify a file system type

I tried 
-t ext3
but it tells me that device or mount point is busy
that is not true
both are free and available
I am the only one on this system.
I am only using 1 console.

Sp what file system "type" could it be for a Linux LVM partition?

---

### Post by merlinus on 2007-08-14
sudo mount /dev/sdax /media/sdax -t ext 3 defaults [SIZE=-1]nls=utf8,umask=0222[/SIZE]

where x is the partition in sda, for example.

OTOH, perhaps the partition is already mounted?

```

mount

```

-merlin

---

### Post by boondocks on 2007-08-14
Ok.  I tried this:

sudo mkdir /mnt/hdb1
sudo mount  /dev/hdb2   /mnt/hdb1    -t ext3   -o defaults,nls=utf8,umask=0222

It says:
mount:  /dev/hdb2  already mounted   or  /mnt/hdb2  busy

But that is not true.  Simply issuing the mount command shows that there is not hdb2 mounted.
Also, I tried df -H and it shows no hdb2

And /mnt/hdb1 is not being used because I just created before issuing the sudo mount .... command.
Again, df -H shows no /mnt/hdb1 being used anywhere.

I have checked repeatedly and there are no signs of the /dev/hdb2 partition being already mounted.

I am still stuck.  :(

---

### Post by moore.bryan on 2007-08-14
*how about ```
sudo mount -t auto /dev/sdb2 /mnt/hdb1
```?*

---

### Post by boondocks on 2007-08-14
Thanks for all the help.

I found the answer here:
[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=1276&start=0](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=1276&start=0)

Specifically, the following applies to my case:

[COLOR="Blue"]You do not mount an LVM partition directly. This is a container holding the data for the logical partitions, which are what you need to mount. type "lvdisplay" to see a list of your logical partitions. each one will have a device name in the form /dev/volume-group/volume-name. Use that to mount the logical volume, e.g.

mount /dev/vg0/vol1 /mnt/somewhere
[/COLOR]

That did it.

---

### Post by moore.bryan on 2007-08-15
*i'm glad you found an answer... lvm seems so complicated sometimes. ;-)*

---

