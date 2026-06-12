---
title: "Acer laptop drive D:\ locked to linux?"
date: 2011-11-18
forum: Hardware
---

### Post by Garland Fox on 2011-11-18
I have a dual boot Vista Home Premium / 11.10 Oneiric Acer laptop.
Windows drive D:\  (linux sda3 partition) has 3 GB of data (recovery use).

That leaves 32 GB of unused space in the partition. NTFS partition.

In windows I can create folders and files in this space. The recovery data is hidden.

In linux I can read but cannot write to this partition.
Linux announces the drive is locked.

I have tried changing the permission but is not allowed.

Need answer how I could unlock this so I can use this space for linux data storage.

Thanks from a newbie.
I don't know anything about permissions.

---

### Post by Garland Fox on 2011-11-18
[ATTACH]207481[/ATTACH]
I attached gparted from that laptop.
The sda3 partition is the one I cannot access from linux.
Error message says do not have permission.
Error message when I try to change permissions says "The DRIVE" is locked.
Any clues how I might gain R&W access to this drive from linux?
Thanks
Newbie

---

### Post by Garland Fox on 2011-11-19
I found the tutorial re permissions changed by editing fstab file.
I will post the file here - I tried both of the bottom lines one at a time.
Either one mounts the Windows partition "DATA" as advertised but the permissions remain read-only.
   Can anyone tell me what I did wrong?

fstab:


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d6a25a94-938a-4357-bf6b-7dd074a99bf5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3b471797-c23d-4488-81dd-4900d693641c none            swap    sw              0       0
# following line attempts to allow permissions to the windows D:\DATA drive on /dev/sda3...
#UUID=A478C52578C4F6D8 /media/DATA ntfs defaults,auto,uid=1000,gid=1000,umask=002 0 0
# try this for alternate device naming
/dev/sda3 /media/DATA ntfs defaults,auto,uid=1000,gid=1000,umask=002 0 0


```I did create an empty folder named "DATA" at /media/DATA to accomodate the mount point.
Maybe folder name causes conflict - don't know - any ideas?

---

### Post by dandnsmith on 2011-11-19
That partition is, I think, a recovery partition, put there at source to allow recovery of the Windows OS.
If you're sure you will never need it, then the best policy is to delete the partition, recreate it as a linux(?) data partition formatting it suitably.
You should be sure of this before you do it, as Acer will wipe their hands of it if you later try to invoke their help.
It's possible that you could save the partition with suitable software - but, my experience says, you probably won't be able to use the saved stuff as it depends on a link which gets broken by deleting the partition, and isn't automatically restored.

HTH

---

### Post by Garland Fox on 2011-11-19
I kind of follow what you are saying. I had a faulty linux partition on another machine that I formatted to NTFS hoping to access with both windows and linux. Same result now: I can access it with windows but linux shows locked out - read only. and this partition was never part of a windows install.

Somewhere I am missing something... Thanks

---

### Post by Garland Fox on 2011-11-20
Mission accomplished.
Thanks to the HOWTO: by WorMzy... got it done.
ntfs-3g reads the windows ntfs partitions.
Thanks all, Thanks WorMzy

---

