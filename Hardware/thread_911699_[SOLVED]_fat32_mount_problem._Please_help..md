---
title: "[SOLVED] fat32 mount problem. Please help."
date: 2008-09-05
forum: Hardware
---

### Post by isdonisgood on 2008-09-05
Hi all,

I have a maxtor external hard drive that has 4 partions. All of them are fat32. they used to mount fine. They show up in Computer but when i try to mount them i get the following error:

The volume 'NEW VOLUME' uses the FAT32 file system which is not supported by your system.

Also sudo fdisk -l does nothing if that helps

This is the result of sudo blkid

kasper@kasper-desktop:~$ sudo blkid
/dev/ps3da1: LABEL="/" UUID="df11b18b-f32e-42de-a9c9-d77ad19a0f80" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ps3da5: TYPE="swap" UUID="bf82d05c-9ae4-435c-96d7-07103501e6d5" 
/dev/sda1: LABEL="NEW VOLUME" UUID="ECDE-679A" TYPE="vfat" 
/dev/sda2: LABEL="CKLOVE" UUID="9C49-B5AA" TYPE="vfat" 
/dev/sda3: UUID="48B4-13AA" TYPE="vfat" 
/dev/sda4: UUID="a611148e-5551-4462-a5d8-bf79899cf9e7" TYPE="ext2" 
kasper@kasper-desktop:~$ 

Also the partions show up in gparted.

I can provide more info if you like. I have tried to fix it myself but I am out of ideas.

Your help would be appreciated and thanks for taking the time to read this!

Kasper

---

### Post by lucho64 on 2008-09-05
Try on a terminal:
```

sudo modprobe vfat

```
I suspect that's not going to work, otherwise the kernel should have loaded the modules already, but it's worth a try

---

### Post by isdonisgood on 2008-09-05
> **lucho64 said:**
> Try on a terminal:
```

sudo modprobe vfat

```
I suspect that's not going to work, otherwise the kernel should have loaded the modules already, but it's worth a try



Thanks. Just tried it out and nothing happened.

kasper@kasper-desktop:~$ sudo modprobe vfat
[sudo] password for kasper:
kasper@kasper-desktop:~$

Tried to mount afterwards and same error occurred.

---

### Post by Bakon Jarser on 2008-09-06
Can you mount them with the live cd?

---

### Post by isdonisgood on 2008-09-06
Hi,

I seemed to have fixed the problem by going onto properties and volume tab, then settings. I gave it the mount point as "media" and type as vfat. It then let me mount as per normal.
Thanks for your help.

Kasper

---

