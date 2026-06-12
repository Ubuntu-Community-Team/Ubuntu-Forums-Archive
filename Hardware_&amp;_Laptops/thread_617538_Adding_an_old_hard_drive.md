---
title: "Adding an old hard drive"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by bluefightingcat on 2007-11-19
Hi,

I recently built a new computer. I added my old IDE hard drive (new one is Sata) to my new system so that I can extract old files from it. After that I plan to get rid of it since I don't need it. 

I managed to connect it and Kubuntu boots fine. However when I try and access the hard-disk (containing 3 partitions: nfts; /; /home;) it doesn't allow it. All I get is the error telling me:

ha1-storage-fixed mount refused uid 1000

Anybody know what this means? and how to fix it?

BFC

---

### Post by taurus on 2007-11-19
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by bluefightingcat on 2007-11-19
Hi,

Here are the details. As you can see the hda hard-drive is recognised (it works in Windows). However for some reason it seems not to be mounted or something in Kubuntu. 



> Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe065e065

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5786    46476013+   7  HPFS/NTFS
/dev/hda2            5787        6151     2931862+  82  Linux swap / Solaris
/dev/hda3            6152        7365     9751455   83  Linux
/dev/hda4            7366       12161    38523870   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05c705c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       13513     6144862+  82  Linux swap / Solaris
/dev/sda3           13514       16063    20482875   83  Linux
/dev/sda4           16064       30401   115169985   83  Linux


My /etc/fstab :

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7493f-8a3f-4215-82d8-ad6e301ea8df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=ec4dccd0-2202-4575-b4df-3c56d46e6df4 /home           ext3    defaults        0       2
# /dev/sda1
UUID=183033FE3033E204 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=0d62a947-bb9a-4cdb-b033-4047804a5fc6 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Any idea how I can fix this?

BFC

---

### Post by taurus on 2007-11-19
Open a terminal and run

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hda1 /media/hda3 /media/hda4
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
sudo mount -t ext3 /dev/hda3 /media/hda3
sudo mount -t ext3 /dev/hda4 /media/hda4
df -h
```

---

### Post by bluefightingcat on 2007-11-19
Hi,

Thanks for the advice. It worked perfectly. I was just wondering is there a way to make them auto-mount when I start up Kubuntu? 

Once I'm done with the hard-disk will simply unplugging it "make it disappear" from my system? 

BFC

---

### Post by taurus on 2007-11-19
If you want to mount those partitions when you boot Ubuntu, add the entries in /etc/fstab.

```
kdesu kate /etc/fstab
```

```
/dev/hda1   /media/hda1   ntfs-3g   defaults   0   0
/dev/hda3   /media/hda3   ext3   defaults   0   0
/dev/hda4   /media/hda4   ext3   defaults   0   0
```
And if you decide to remove the harddrive, you need to remove those three lines from your /etc/fstab as well.

---

### Post by bluefightingcat on 2007-11-20
Hi,

Thanks a million for the advice! Appreciate it! =D>

---

