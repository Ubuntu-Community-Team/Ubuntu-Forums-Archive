---
title: "Lost almost 500GB of new 3TB drive!"
date: 2011-06-29
forum: Hardware
---

### Post by WildZontar on 2011-06-29
I used Gparted to format my new 3.0TB drive, with the "gpt" partition table and ext4 filesystem. 

To my shock, a LOT of space on the new format was lost! Gparted shows 44GB used (out of a maximum drive size of 2.73TB). GNOME says I have 139.9 GB used with 2.5 out of 2.7TB free.

Is this normal overhead or did I format it wrong?

---

### Post by WildZontar on 2011-06-29
Also...I have no permission to do anything at all on the drive. How do I take ownership of a whole drive?

---

### Post by oldfred on 2011-06-29
MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Have you mounted partition and set ownership and permissions?

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Best to mount in fstab, but to manually mount:
sudo mkdir /data
sudo mount /dev/sdb1 /data
#where sdb1 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -lu

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions. 777 is read, write & execute by everyone
sudo chmod -R 777 /data
sudo chown -R $USER:$USER /data
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by dabl on 2011-06-29
I assume you're using the 64-bit OS?  Because 32-bit Linux is limited to 2TB (unless you have LFS support):

[http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html](http://www.cyberciti.biz/tips/what-is-maximum-partition-size-supported-by-linux.html)

In addition to the excellent background links provide by oldfred, your BIOS may be limiting the size of hard disk drive that your system can "see" (and Linux gets its information about the storages devices from BIOS, mostly):

[http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm](http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm)

---

### Post by psusi on 2011-06-29
> **dabl said:**
> I assume you're using the 64-bit OS?  Because 32-bit Linux is limited to 2TB (unless you have LFS support):

The Ubuntu kernels have that enabled.

> **dabl said:**
> 
In addition to the excellent background links provide by oldfred, your BIOS may be limiting the size of hard disk drive that your system can "see" (and Linux gets its information about the storages devices from BIOS, mostly):

No it does not; the kernel talks directly to the hardware with no help from the bios, which only operates in 16 bit mode.  If the bios can't see the whole disk, it can cause problems booting from it, but not beyond that.

---

### Post by Yellow Pasque on 2011-06-29
> [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
That.
> your BIOS may be limiting the size of hard disk drive that your system can "see"
If that was the case, it wouldn't be 2.7GB..

---

### Post by Jose Catre-Vandis on 2011-06-29
You can set the number of reserved blocks to free up some space (normally 5%). Running the following command should reduce reserved blocks to 2%. You can do this on a formated filesystem.
```
sudo tune2fs -m 2 /dev/sdxx
``` where sdxx is the letter and number of your partition, e.g. sda1.

---

### Post by dabl on 2011-06-29
> **psusi said:**
> The Ubuntu kernels have that enabled.

No it does not; the kernel talks directly to the hardware with no help from the bios, which only operates in 16 bit mode.  If the bios can't see the whole disk, it can cause problems booting from it, but not beyond that.

> **Temüjin said:**
> That.

If that was the case, it wouldn't be 2.7GB..


OK fine -- color me and my ignorance stomped on. It looks like our OP actually did get some useful help, from Jose Catre-Vandis.  You go, Jose!  :D

---

