---
title: "lost detected hard drive memory after upgrade... normal?"
date: 2016-01-24
forum: Hardware
---

### Post by anotherChris on 2016-01-24
I have a Dell laptop with a 160 GB hard drive.  I was running Lubuntu 11.10 on it and had ?? GB data.  It used to show
```

Free space: 135.X GB (Total: 15X.X GB)

```

Recently, I upgraded to Lubuntu 15.10 and had it erase the disk and freshly install and, despite the fact I haven't loaded any of my files back onto the hard drive, it now shows
```

Free space: 133.8 GB (Total: 144.7 GB)

```

I know Lubuntu can fit on a 4GB hard drive, so it must not use more than a few GB of space.  What happened to the memory on my hard drive?  Is it normal to lose some every time you install a new OS (I can't think why)?

Thanks.  (Obviously, I don't know much about computers...)

---

### Post by Yellow Pasque on 2016-01-24
Maybe the installer selected a larger swap space since the 11.10 days? Look at:
```
sudo fdisk -l
```

---

### Post by anotherChris on 2016-01-24
> **Temüjin said:**
> Maybe the installer selected a larger swap space since the 11.10 days?

I have no idea about swap space, but here is the readout from the command you suggested:

```

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x81040ad0


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 308463615 308461568 147.1G 83 Linux
/dev/sda2       308465662 312580095   4114434     2G  5 Extended
/dev/sda5       308465664 312580095   4114432     2G 82 Linux swap / Solaris

```

So, see anything?

---

### Post by Yellow Pasque on 2016-01-24
> So, see anything? 
Nothing unexpected. Come to think of it, 160 GB = ~149 GiB, so the current output looks spot on. I'm not sure how you saw 15x GiB when you were running 11.10.

---

### Post by anotherChris on 2016-01-24
> **Temüjin said:**
> Come to think of it, 160 GB = ~149 GiB

Hmmm... I don't anything about this stuff.  But also I was previously at 135 GB free space *with* all my GB of files on the computer.  They are now sitting on a USB flash drive, but I am down to 133 GB *without* any saved files.  So it seems like my free space has been reduced by 15-20 GB... I guess it doesn't really matter, just strange to me.  Anyway, thanks.

---

### Post by Yellow Pasque on 2016-01-24
It depends on what packages you have installed, how many old kernels you have installed, how many packages are in the cache, etc.
Trying to compare free space between two installs of different versions seems pointless to me. *shrug*

---

### Post by anotherChris on 2016-01-24
> **Temüjin said:**
> It depends on what packages you have installed, how many old kernels you have installed, how many packages are in the cache, etc.
Trying to compare free space between two installs of different versions seems pointless to me. *shrug*

OK.  I don't know about it.  Also, I noticed in Preferences-->Disks that I have Extended Partition 2.1GB, Swap Partition 2.1GB, and Filesystem Partition, 158GB (151GB free).  So I don't know where those other readings come from, but 151GB free seems to me like what I should have.

Case closed.

---

