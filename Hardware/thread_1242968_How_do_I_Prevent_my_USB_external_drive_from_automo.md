---
title: "How do I Prevent my USB external drive from automounting?"
date: 2009-08-17
forum: Hardware
---

### Post by Stochastic on 2009-08-17
I'm attempting to do some maintenance work on my external USB drive, and one of the partitions won't unmount once it's mounted.  So I'd like to turn off automounting of my USB drives.  Any idea how to get this done?

---

### Post by vinnywright on 2009-08-17
> one of the partitions won't unmount once it's mounted```
sudo umount /dev/the partition
```will unmount it..................like.......sudo umount /dev/sda1 .....would unmount the first partition of /sda 

do in a terminal

```
fdisk -l
``` that's a lower case L not I

to see what the /dev entry for the disk (or partition on the disk) should be :)

dont know how you got auto mounting on so I dont know how to tell ya to turn off

if it's auto mounting becos it's in fstab remove the ofending line .....but youll half to manualey mount it thar after..............of corse thats just a click if it's displayd in your file manager :)

O ya I think those thing's auto mount if thare pluged in during boot............boot with it unpluged and see.

VINNY

---

### Post by Stochastic on 2009-08-18
Nope, Ubuntu auto mounts USB storage devices always (unless you've got a server edition running).

And I've tried manually unmounting the partitions, and the device via both the command line and nautilus.  It hangs.

I need to plug this thing in, not have it mount on me, then run fsck on it to fix the thing.

---

