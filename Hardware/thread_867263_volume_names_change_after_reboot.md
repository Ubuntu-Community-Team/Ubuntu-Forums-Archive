---
title: "volume names change after reboot"
date: 2008-07-22
forum: Hardware
---

### Post by noogs on 2008-07-22
I have three main volumes that i keep connected all the time. One is my filesystem and on the same hard drive i have another partition this hard drive switches names with a second hard drive i have. For instance my filesystem is either /dev/sda2 or dev/sdb2. My second partition may be either /dev/sda1 or /dev/sdb1. While my other hard drive will be the opposite of my second partition. This causes problems because while my filesystem always mounts correctly my other partition and second hard drive switch mount places on almost each boot. Please help this is getting really annoying.

---

### Post by jocko on 2008-07-22
> **noogs said:**
> I have three main volumes that i keep connected all the time. One is my filesystem and on the same hard drive i have another partition this hard drive switches names with a second hard drive i have. For instance my filesystem is either /dev/sda2 or dev/sdb2. My second partition may be either /dev/sda1 or /dev/sdb1. While my other hard drive will be the opposite of my second partition. This causes problems because while my filesystem always mounts correctly my other partition and second hard drive switch mount places on almost each boot. Please help this is getting really annoying.

That's normal, device nodes often changes from boot to boot.
You should make sure the file systems are mounted by their uuid instead of their device nodes (uuid's are unique identifiers that are specific for each specific partition).

To find the uuid's for your partitions, type this in a terminal:
```
ls -la /dev/disk/by-uuid
```That will get you a list with lines similar to this one:
```
lrwxrwxrwx 1 root root  10 2008-07-22 23:33 [COLOR=Red]f394b2f2-4d6e-40cc-a64a-9ffe04b63935[/COLOR] -> ../../[COLOR=Black]sda1[/COLOR]
```The string I have highlighted in red is the uuid for one of my partitions, and this particular boot it has the device node /dev/sda1.

Now edit your /etc/fstab:
```
gksudo gedit /etc/fstab
```...and change the device nodes (/dev/sdxY) at the beginning of the entry for each of your disk to "[COLOR=Blue]UUID=[/COLOR]" followed by the correct uuid (I'm sure your root  (/) file system is already mounted like this, as this has been the default way a couple of years).

So to make sure this partition is always mounted in the same place, my /etc/fstab has this line:
```
[COLOR=Blue]UUID=[/COLOR][COLOR=Red]f394b2f2-4d6e-40cc-a64a-9ffe04b63935[/COLOR] /media/120GB    ext3    defaults        0       2
```insted of this:
```
[COLOR=Blue]/dev/sda1[/COLOR] /media/120GB    ext3    defaults        0       2
```

---

### Post by noogs on 2008-07-22
Thanks it worked like a charm.

---

