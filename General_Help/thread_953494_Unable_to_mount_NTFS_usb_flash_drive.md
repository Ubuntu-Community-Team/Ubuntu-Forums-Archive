---
title: "Unable to mount NTFS usb flash drive"
date: 2008-10-20
forum: General Help
---

### Post by Julian David Pitt on 2008-10-20
When I insert a usb flash drive I get the following error, please see attached screen shot. I have googled around and searched these forums but so far have found nothing that works for me. Many thanks.

---

### Post by alphaniner on 2008-10-20
I just tried mounting an NTFS-formatted flash drive and I had no problem.  I'm also running Hardy.  Mounting it as root from the terminal failed?

---

### Post by Julian David Pitt on 2008-10-23
> **alphaniner said:**
> I just tried mounting an NTFS-formatted flash drive and I had no problem.  I'm also running Hardy.  Mounting it as root from the terminal failed?

It will not mount as root either, I just get told that /dev/sdb1 does not exist. I also have checked that I have "use fuse filesystems" permission. Any further ideas please?

---

### Post by drs305 on 2008-10-23
> **Julian David Pitt said:**
> It will not mount as root either, I just get told that /dev/sdb1 does not exist. I also have checked that I have "use fuse filesystems" permission. Any further ideas please?

Removable drives sometimes change their designations. With the usb device plugged in, run the following command to determine which devices the system is seeing. The device might be listed as /dev/sdc1 or something other than sdb1. Note the command is a small L.
```
sudo fdisk -l
```

You also might try re-installing ntfs-3g.

---

### Post by Julian David Pitt on 2008-10-27
Sorry it has been a while since I had chance to do more on this but I have now and this is what I get at the fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94f9ffe4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1043 MB, 1043333120 bytes
216 heads, 11 sectors/track, 857 cylinders
Units = cylinders of 2376 * 512 = 1216512 bytes
Disk identifier: 0xbed21ba4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         858     1018841+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 5, 9)
Partition 1 has different physical/logical endings:
     phys=(126, 215, 11) logical=(857, 137, 7)
```
It appears that the drive is recognised but does not want to be mounted automatically at insertion but can be mounted in a terminal,but only as root. Your thoughts would be appreciated, thanks.

---

### Post by alienprdkt on 2008-10-27
#sudo apt-get install pmount
#sudo apt-get install ntfs-3g
reboot

If auto-mount failed  you can try to mount your external drive manually with this command:

sudo pmount-hal /dev/sda1
Please replace /dev/sda1 with your external hard drive. You can find out about it by running

sudo fdisk -l | grep NTFS

If the ntfs drive is not mounted automatically open /etc/modules file & add 'fuse' in a new line. This will load the fuse module.

eg:  

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse

---

### Post by Julian David Pitt on 2008-10-28
```
#sudo apt-get install pmount
#sudo apt-get install ntfs-3g
```

Both already installed

```
sudo pmount-hal /dev/sdb1
```

Above gives me 

```
julian@Hardy:~$ sudo pmount-hal /dev/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

```
sudo fdisk -l | grep NTFS
``` takes me back to the prompt
I have checked /etc/modules and fuse is already there?
I take it the signature issue is the problem but how is that fixed from here please? I should point out that the current USB pendrive I am using is only Fat16 but I will try another NTFS one tomorrow.

---

### Post by alienprdkt on 2008-10-29
> **Julian David Pitt said:**
> I should point out that the current USB pendrive I am using is only Fat16 but I will try another NTFS one tomorrow.
 :lolflag::lolflag:

 sudo mount -t vfat <device> <mount_point>

---

