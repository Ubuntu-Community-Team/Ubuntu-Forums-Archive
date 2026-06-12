---
title: "How to make Feisty detect/mount my SATA Hard Disk?"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by gothica on 2007-06-03
I have this very frustrating problem (at least for me). So here's the story. Before, i have Windows installed in my SATA hd. Then i got an ATA hd and installed Feisty there. At first, Feisty could detect my SATA hd. Then i thought of reformatting both hds. So after formatting, i installed once again Feisty on my ATA hd. However, when i booted up Feisty it no longer detects/mounts my SATA hd. I'm not very good with hardware configurations so please help me out. I'd really appreciate it.

---

### Post by taurus on 2007-06-03
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Otherwise, here is something for you to read, [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G).

---

### Post by gothica on 2007-06-05
thanks for the reply.
i already have solved this problem. i just recompiled to the latest kernel (2.6.21.3) and everything worked perfect for me.

---

### Post by flatbeard on 2008-03-06
I have the same problem. I have a fresh Ubuntu 7.10 desktop on a HP system with 2x9GB SCSI harddisks, running fine. But Ubuntu can't see my 160 GB SATA harddisk.

fdisk -l shows me that the SATA harddisk exists:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x530a530a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux
```

And then the two 9GB's as /dev/sdb and /dev/sdc

But what do I do? I've tried to mount /dev/sdb, but I'm not sure I speak the spells correctly. I get errors like "fstab doesn't know what the hey you're talking about". I don't know how to do anything with the kernel (as someone else did), I'm way to much of a newbie.

I would like to mount the drive so that I can put a virtual machine from VMWare on the separate drive. The current path for VMWare VM's is /var/lib/vmware/Virtual Machines, and I'd like to mount the SATA in /var/lib/vmware. Perhaps even as a replacement for the /Virtual Machine-dir, which at present is empty.

Man... for a newbie I sound technical! \\:D/ But I'm really not. I'm rather new to Linux, and hope to invoke nothing more than a Ubuntu / VMWare basis for my Exchange server.

Help ... (whine)

---

### Post by taurus on 2008-03-06
> **flatbeard said:**
> I have the same problem. I have a fresh Ubuntu 7.10 desktop on a HP system with 2x9GB SCSI harddisks, running fine. But Ubuntu can't see my 160 GB SATA harddisk.

fdisk -l shows me that the SATA harddisk exists:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x530a530a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux
```

And then the two 9GB's as /dev/sdb and /dev/sdc

But what do I do? I've tried to mount /dev/sdb, but I'm not sure I speak the spells correctly. I get errors like "fstab doesn't know what the hey you're talking about". I don't know how to do anything with the kernel (as someone else did), I'm way to much of a newbie.

I would like to mount the drive so that I can put a virtual machine from VMWare on the separate drive. The current path for VMWare VM's is /var/lib/vmware/Virtual Machines, and I'd like to mount the SATA in /var/lib/vmware. Perhaps even as a replacement for the /Virtual Machine-dir, which at present is empty.

Man... for a newbie I sound technical! \\:D/ But I'm really not. I'm rather new to Linux, and hope to invoke nothing more than a Ubuntu / VMWare basis for my Exchange server.

Help ... (whine)

I don't see any /dev/sdb or /dev/sdc from the output above?  Are you sure you have them plugged in and on?

---

### Post by flatbeard on 2008-03-07
> **taurus said:**
> I don't see any /dev/sdb or /dev/sdc from the output above?  Are you sure you have them plugged in and on?

Here's where the newbie shows ... what's that? :?:
I also tried this, composed from the man page: 
```
 sudo mount -v -t auto /dev/sda /etc/vmware 
```
And it gave me this:
```
 mount: you didn't specify a filesystem type for /dev/sda
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: you must specify the filesystem type 
```

The harddisk is etc3-format (I formatted the thing with Gnome Partition Editor (Gparted).

---

### Post by flatbeard on 2008-03-07
Hm. I just found the hard disk in /media while sniffing about (I'm in the GUI now). It was unmounted, so I selected "mount" and can now access it as /media/disk. (it hasn't been there before, afaik...)
It's not perfect, but it's there.

Only thing is, when I enter "ls -l" the output is this: drwxr-xr-x 3 root root 4096 2008-03-05 23:13 disk
I would like to have full read/write rights, as I am not sure what will happen if I run VMWare as a standard user and tell it to use /disk as the data directory with all the virtual machines on. Without the read/write-rights.

It's chmod something, but "sudo chmod +rwx disk" doesnt do anything.
I can also enter the disk, make a dir ("sudo mkdir vmware") but again, only root has write rights. Sudo chmod again does nothing.

(maybe someone can move this thread to "beginners corner"?)  :-k

---

