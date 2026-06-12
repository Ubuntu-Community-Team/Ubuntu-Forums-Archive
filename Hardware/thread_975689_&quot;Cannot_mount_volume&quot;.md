---
title: "&quot;Cannot mount volume&quot;"
date: 2008-11-08
forum: Hardware
---

### Post by Big4wheeler on 2008-11-08
Hey guys, I recently switched to Ubuntu, 8.04. When I try to access a internal HDD different then the one I have installed ubuntu to I get a error "Cannot mount volume - Unable to mount the volume 'OS'." (Its called OS due to XP being installed on it).

Output of sudo fdisk -l

> Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe8dbe8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25ab70f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS


Thanks for any help!

---

### Post by taurus on 2008-11-08
Are you trying to mount /dev/sdb1?  Install ntfs-config and use it to mount your /dev/sdb1 then.

Applications -> Accessories -> Terminal
```
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Big4wheeler on 2008-11-08
> **taurus said:**
> Are you trying to mount /dev/sdb1?  Install ntfs-config and use it to mount your /dev/sdb1 then.

Applications -> Accessories -> Terminal
```
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Thanks for the reply, I just installed that, and restarted, did not work. Still have the problem.

> Mounting /media/OS failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/OS -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/OS ntfs-3g force 0 0

---

### Post by taurus on 2008-11-08
Try mounting it from a terminal with the force option.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/OS -o force
df -h
```

---

### Post by Big4wheeler on 2008-11-08
> **taurus said:**
> Try mounting it from a terminal with the force option.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/OS -o force
df -h
```

Thanks very much! It worked.

---

