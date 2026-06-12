---
title: "Add new hard disk to an installed system"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by kunalbhate on 2007-08-30
Hello,

I am having Dapper LTS installed.

I want to add new hard disk having 80GB connected to ATA (IDE) interface, which shall be shared among network users. The hard disk should be able to connect to any OS : Windows or Linux independently and easily.

I tried installing it using Fdisk command, but unfortunately couldn't succeed. I think I could not clear MBR, which might have caused the problem.

Could you please list the process how to install it on the system.

Thanks and regards,


Kunal

---

### Post by merlinus on 2007-08-30
Have you formatted and partitioned the disk?

What happened when you used fdisk, and what parameters did you use with the command?

-merlin

---

### Post by kunalbhate on 2007-08-30
The hard disk which I want to add was having XP.

After I connected this hard disk, the system detected it but could not mount. Since I didn't want any data on it. I simply formatted it, and tried to mount. The system could not mount the disk. 

Later I tried formatting using FDISK loaded both the file systems FAT and EXT2 but the system refused to mount it.

Finally, I removed the ubuntu hard disk and plugged this hard disk as master. The ntloader which was present on the hard disk reported the error while booting. 

I think this concludes I could not erase the boot loader (MBR) of the hard disk which might have caused the problem of mounting. (this might be wrong also, this is my guess.)

---

### Post by lenniboy on 2007-08-30
You probably didn't create a file system inside your partition.

Try using Gparted. It's an easy to use GUI to the parted library.

```
sudo apt-get install gparted
```

You can then find it in System->GNOME Partition Editor or just run "gparted" from the console.

---

### Post by kunalbhate on 2007-09-03
hello,

This weekend I spent on connecting the hard disk, but I couldn't succeed.

I formated it seperately and interfaced, but ubuntu refused to mount.

I removed the main OS (ubuntu) Hard Disk from the system.
I loaded OS (ubuntu) on the hard disk which I wanted to interface with main system.
Connected the main hard disk and booted the system with Ubuntu, and then tried to mount another harddisk. The system showed in the Disk in the Disk Menu, but refused to mount.

I tried with Gparted, it showed all partitions on the hard disk. I deleted both the partitions using gparted and created/formated them but main system REFUSED to mount the slave hard disk.

what could be the reson behind it...?
Does Linux/Ubuntu support multiple hard disks...?

Where can I find more information on it..?

Thanks and regards,


Kunal

---

