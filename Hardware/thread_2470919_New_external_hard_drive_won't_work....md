---
title: "New external hard drive won't work..."
date: 2022-01-16
forum: Hardware
---

### Post by aleph04 on 2022-01-16
Ok... So I can get this drive to be recognized via sudo fdisk -l (sometimes)... but it won't mount. I can't use gparted on it (freezes it up) and I can't format it to anything other than exfat. Anyone know of any utility I can use (not parted, gparted, fdisk) to take a closer look and maybe get this thing working? 
 
It's 2 TB... That's the only thing I can think that would be causing all of this. It's small and 2 TB lol.

---

### Post by aleph04 on 2022-01-16
I tried to do something with dd with it, and now it's not recognized at all. I tried to clone my hard disk from my laptop onto it to be able to boot from it. And now... nothing.

---

### Post by ajgreeny on 2022-01-16
And those times when fdisk does see the disk, tell us exactly the output of the command is; without more details there's not much more we can tell you to do.

---

### Post by aleph04 on 2022-01-16
Unfortunately, it no longer shows up and I don't know what to do.

---

### Post by oldfred on 2022-01-16
USB power or separate power supply?
Many USB hard drives need more power than USB port can provide.

---

### Post by aleph04 on 2022-01-16
I actually found it in disks... but it's not coming up in fdisk -l. Can't format it.

---

### Post by TheFu on 2022-01-16
If the BIOS doesn't always see the disk, it is hardware failing, somewhere.
If the BIOS does always see the disk, I'd check the SMART data for it and see if that leads to something.
Also, if you know the current device for the GPT partition, you can directly format it to a file system with a command like this:
```
sudo mkfs -t ext4 /dev/sdX1
```
Of course, this makes all sorts of assumptions which might not be true.
Things like it has a partition table already.
The partition table is GUID and valid.
There is at least 1 partition in the partition table.  Now is the time to make smaller partitions, if this is for an OS drive. Or if you want to use ZFS or LVM, now is the time to make that happen.

Intermittent issues are usually loose cables - power or SATA or SAS.  Hopefully this isn't USB, since USB doesn't support the full SATA command set and we won't be able to access all the data that a drive has over a USB connection.

---

### Post by ajgreeny on 2022-01-17
Do you have another machine or operating system you can attach the disk to?
That might be able to see it.
What about the USB cable you are using; do you know it is a good one?

---

### Post by tea for one on 2022-01-18
> **aleph04 said:**
> I actually found it in disks... but it's not coming up in fdisk -l. Can't format it.

Have you tried to use the tools in Disks (gnome-disk-utility)?

Here is some info [https://linuxhint.com/gnome_disk_utility/](https://linuxhint.com/gnome_disk_utility/)

---

### Post by TheFu on 2022-01-18
**fdisk** doesn't format anything. It can be used for putting a partition table (mbr or gpt) and for partitioning.  **gparted** is much easier.
I've not used gnome-disks, ever.

I tend to use gdisk, sgdisk and cgdisk for this stuff these days in my pre-installation disk setup tasks.  Most people would use gparted.

There are lots of ways to do this stuff, but the BIOS needs to provide access to the disk for the OS tools to work.

---

