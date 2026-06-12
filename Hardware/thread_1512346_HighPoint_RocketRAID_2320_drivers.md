---
title: "HighPoint RocketRAID 2320 drivers"
date: 2010-06-18
forum: Hardware
---

### Post by lukeiamyourfather on 2010-06-18
It seems like my RAID card is not recognized by Ubuntu 10.04 LTS and I don't find anything in the repositories for it. The card is a HighPoint RocketRAID 2320 (8 port SATA to PCI-Express). There should be something listed by fdisk like a 900GB RAID 5 array and 1.5TB RAID 5 array, but only the 150GB Raptors and 400GB drives show up.

```

lukeo@amdahl:~$ apt-cache search hpt
dmraid - Device-Mapper Software RAID support tool
lukeo@amdahl:~$ apt-cache search highpoint
dmraid - Device-Mapper Software RAID support tool
lukeo@amdahl:~$ apt-cache search rocketraid
lukeo@amdahl:~$ 

```

```

lukeo@amdahl:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x221f00db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10e2ab97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1992    15998976   82  Linux swap / Solaris
/dev/sdb2   *        1992       48642   374711296   83  Linux

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x020f0a9c

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ccb8267

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       36481   293033601    7  HPFS/NTFS
lukeo@amdahl:~$ 

```

HighPoint's site has drivers up to Ubuntu 9.04 and a source code driver that hasn't been updated in a while and doesn't say its supports the kernel version in Ubuntu 10.04 LTS. Any suggestions about the best way to get it working on Ubuntu 10.04 LTS? Anyone have this card and have it working already? Hopefully there's a way to get it working, not like its a bleeding edge new RAID card. Thanks for your help!

---

### Post by lukeiamyourfather on 2010-06-18
Bump! :confused:

---

### Post by lukeiamyourfather on 2010-06-19
I've installed the drivers from source and things seem to be working right now. Though I'm worried if there's a kernel update that my drivers will break. Is this correct that a kernel update will break the drivers? If so is there a way to have the drivers rebuild when there's a kernel update?

---

### Post by lukeiamyourfather on 2010-07-26
The driver did break after a kernel update. The system still booted though which is what I was really worried about. Running the script to build the module again automatically removes the old module so it wasn't too bad. Still hoping there's an automatic way to do this though.

---

### Post by icydee on 2010-08-27
Hi
I have been struggling for a while to get a distribution/driver combination that works.

I see you have upgraded your kernel version, may I ask which version? If possible, would you be able to provide pre-built drivers that I could use with instructions on how to install them please?

Regards
Ian

---

### Post by lukeiamyourfather on 2010-08-27
> **icydee said:**
> 
If possible, would you be able to provide pre-built drivers that I could use with instructions on how to install them please?


I don't mind helping people out, but providing a complied driver with an installer is really the job that HighPoint should be doing (and its a shame they aren't doing it anymore!). The source drivers come with directions that are pretty easy to follow. You need to install a complier like GCC and the kernel headers (for whatever kernel you have). The source code for the driver is below.

[http://www.support-highpoint-tech.com/Main/rr232x/Linux/opensrc/rr232x-linux-src-v1.10-090716-0928.tar.gz](http://www.support-highpoint-tech.com/Main/rr232x/Linux/opensrc/rr232x-linux-src-v1.10-090716-0928.tar.gz)

If you are unable to get it to work I suggest contacting HighPoint support and ask for a driver for the version of Ubuntu you are using. Another avenue would be to make a feature request for Ubuntu to include the drivers in future versions, but that won't help you much right now. Cheers!

---

