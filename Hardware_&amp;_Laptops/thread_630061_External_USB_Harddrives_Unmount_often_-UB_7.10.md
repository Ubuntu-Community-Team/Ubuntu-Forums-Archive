---
title: "External USB Harddrives Unmount often -UB 7.10"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by sebutler2 on 2007-12-02
Hello.. I am running UB 7.10 and I have multiple usb devices connected to my system.. In particular I have two USB external hardrives (maxtor 80GB & WS 250GB) directly connected to my computer.  Very frequently these drives unmount from my system and can not be remount unless I power cycle them.

Any suggestions on how I can keep them mounted? And is this a os issue?

---

### Post by bwald on 2007-12-02
Post the contents of your /etc/fstab file.  This is the file that tells the system which drives to mount at startup, and might give a clue as to your problem.

---

### Post by sebutler2 on 2007-12-02
here is my /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9307d87a-0f65-468b-9123-dfc885ab363b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=857ded0c-1919-4d65-981c-5e59ea1f66da none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Currently the usb drives are not mounted.

---

### Post by bwald on 2007-12-03
When you mount the USB drives, do you know which device they are located under?  i.e. according to your fstab, your main filesystem is located at /dev/hda1 and your swap space is located at /dev/hda5.  Do you know where your USB drives are located at?  If not, plug them in and then type:

```
df -h
```

"df" will list all of the filesystems your system can see, the "-h" flag isn't necessary, it just means "display sizes of filesystems in human-readable format."  Once you know where your devices are located, you can set the fstab to automatically mount them, and this should keep it from unmounting all the time.  I'll give you some example output so you can know what to do.

Lets say you just plugged in the harddrives, then ran "df -h."  You'll see something like this:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1               73G  1.7G   67G   3% /
/dev/hdb               99M   34M   61M  36% /media/hdb
/dev/hdc               100G   50G   50G  50%  /media/hdc

```

You'll want to add a line for each USB drive to your fstab.  The line should be something like this:

```

/dev/hdb                /media/hdb                    ext3    defaults,noauto       0 0

```

Make sure you know what filesystem the drives are using, and replace "ext3" with the correct filesystem (if ext3 is not right).

---

### Post by sebutler2 on 2007-12-03
Here is the output of my df -h 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   17G   18G  49% /
varrun                379M   96K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M  124K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             1.3G  1.3G     0 100% /media/cdrom1
/dev/sdd5              77G   49G   28G  65% /media/STORAGE-80_
/dev/sdc1             233G   82G  152G  36% /media/My Book_


I have added the following comands to my /etc/fstab 
/dev/sdd5       /media/STORAGE-80_ ntfs  defaults,noauto  0 0
/dev/sdc1       /media/My Book_   vfat   defaults,noauto  0 0

Is it required that I change the mount points or can they remain the same as the pregenerated ones?  Also this should be a standard practice for any drives that required to be always accessible?

---

### Post by bwald on 2007-12-03
You can change the mount points if you want, but you don't have to.  I like to standerdize the naming of them, (i.e. /media/external1, /meda/external2) but that is entirely personal choice.  Remember that if you do change the mount points, make sure you create a directory with that name in the right place before mounting the drive.

In response to your second question, yes this is standard practice for all drives you will regularly use, and even for drives you don't always use.  I added the "noauto" flag for fstab file because that means "if the device doesn't exist (because its not plugged in) don't try to mount it because you'll fail" so you can use this for any drive you'll concievably use.

---

