---
title: "How do I mount LogVol?"
date: 2008-07-20
forum: General Help
---

### Post by hg21 on 2008-07-20
I am a long term RedHat/Fedora user trying Kubuntu.

It would be useful to mount my existing Fedora LogVol partition in Kubuntu.

How can I do this please? What is the filesystem?

====================================
  sudo mount -t ext3 /dev/sda3 /mnt/Fed
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
======================================

---

### Post by RealPSL on 2008-07-20
The first thing you have to do is install lvm2 since it is not installed on the desktop edition by default. At least not in ubuntu.

```
sudo apt-get install lvm2
```

Once that is done you need to make your system aware of the logical volumes and volume groups with

```
sudo vgscan
```

At this point there are a bunch of commands you can run to activate the logical volumes but frankly it is easier just to reboot since it is just your personal desktop. If you are working on a server then let me know and I will go into details

Once the system comes back online you will be able to run 
```
sudo vgdisplay -v
```

Note the volume group your LogVol is in. Note that this is not a regular partition it is a logical volume.

Once you identify the logical volume (if you have difficulty send the vgdisplay -v output). Check the file system for errors. Below assumes that Volume00 is the volume group and LogVol00 is the logical volume

```
sudo fsck /dev/Volume00/LogVol00
```

Mount the file system with 

```
sudo mount -t ext3 /dev/Volume00/LogVol00 /mnt/Fed
```

Adding it to the /etc/fstab file is optional depending on whether you want to keep it mounted.

---

### Post by hg21 on 2008-07-25
Many thanks for your very informative, detailed help. 



> **RealPSL said:**
> The first thing you have to do is install lvm2 since it is not installed on the desktop edition by default. At least not in ubuntu.

```
sudo apt-get install lvm2
```

Once that is done you need to make your system aware of the logical volumes and volume groups with

```
sudo vgscan
```

At this point there are a bunch of commands you can run to activate the logical volumes but frankly it is easier just to reboot since it is just your personal desktop. If you are working on a server then let me know and I will go into details

Once the system comes back online you will be able to run 
```
sudo vgdisplay -v
```

Note the volume group your LogVol is in. Note that this is not a regular partition it is a logical volume.

Once you identify the logical volume (if you have difficulty send the vgdisplay -v output). Check the file system for errors. Below assumes that Volume00 is the volume group and LogVol00 is the logical volume

```
sudo fsck /dev/Volume00/LogVol00
```

Mount the file system with 

```
sudo mount -t ext3 /dev/Volume00/LogVol00 /mnt/Fed
```

Adding it to the /etc/fstab file is optional depending on whether you want to keep it mounted.

---

