---
title: "Can't auto-mount disks no matter what I do"
date: 2013-06-25
forum: Hardware
---

### Post by Rhemat on 2013-06-25
Heya All,

I'm running Lubuntu 13.04 on my server, and just got two 500GB SATA hard drives, but I can't auto mount them.  I've tried using the disks application, but it seems to throw out my settings at random.  I've also tried editing /etc/fstab, but I always get mount errors upon booting up the machine.

Just in case, here is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=bf5b3852-cb5b-496c-903d-885ca40e10f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=22b4cd19-7c73-482b-8bed-7c4f3f049ccd none            swap    sw              0       0
/dev/sda /opt/vol01 ext4 nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/sdb /opt/vol02 ext4 nosuid,nodev,nofail,x-gvfs-show 0 0


```

Any advice would be appreciated.

Thanks in advance.

---

### Post by MidnightGrey on 2013-06-25
Hi Rhemet,

these two lines in your fstab are incorrect
> 

/dev/sda /opt/vol01 ext4 nosuid,nodev,nofail,x-gvfs-show 0 0 
/dev/sdb /opt/vol02 ext4 nosuid,nodev,nofail,x-gvfs-show 0 0


I'm not on my linux system right now so hopefully someone else can come along and give you correct instructions.
but can you post these outputs for now:


sudo blkid

sudo fdisk -l

*that is -l for llama*

---

### Post by Morbius1 on 2013-06-25
First, what MidnightGrey said.

Second, aside from the fact that you are using the rinky-dink "Disks" utility to do this ( x-gvfs-show only shows up in "Disks" ):

**/dev/sda** is the physical hard drive itself.
**/dev/sda1** ( for example ) is a partition on that physical hard drive.

You don't mount a hard drive you mount a partition on that hard drive. A better way is to use UUID's which is what the blkid command will provide to you.

---

### Post by Rhemat on 2013-06-25
Thanks for the answers, I was able to fix it with this here:

```

UUID=3352603d-6253-446e-936b-377f33e51554 /opt/vol01 ext4	auto,user,rw,exec 0 0
UUID=cb2636e9-8a77-438c-9d22-2e883ae258a4 /opt/vol02 ext4 auto,user,rw,exec 0 0

```

The options in the previous post may have been a hurdle, and using the UUID may have been more useful to the machine.

Thanks again.

---

