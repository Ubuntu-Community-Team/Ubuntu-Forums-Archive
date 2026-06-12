---
title: "Problems with a Seagate External HD (surprise, surprise...)"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by enfeiris on 2008-03-16
Hey all - I know this has been posted about before, but the posted solutions either did not work or weren't clear enough for me to follow, so I thought I'd ask again.

I have a 250gb FreeAgent external hard drive.  I was able to prevent the drive from going to sleep by booting into windows (I have a dual boot configuration) and running the Seagate utility.  However, the drive is auto-mounted as read-only and I cannot figure out how to change this.  

The drive is formatted in NTFS.  I'm using 7.04 and am *new to linux*.  I'd appreciate anyone's help with this problem.  Thanks!

---

### Post by unutbu on 2008-03-16
Is this external HD always connected to your computer?

If you say yes, then there is a way to make it mount readable and writable at boot time and I can help you.

If no, do you mind typing a few keys every time you want to mount it?

If yes, then you need the automounter, and unfortunately I do not know how to configure that (though there must be a way...)

If no, I think I can help you.

---

### Post by enfeiris on 2008-03-16
It's always connected to my computer.

---

### Post by unutbu on 2008-03-16
Please post the output to the following terminal commands:
```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by enfeiris on 2008-03-16
sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       30394   233588736    7  HPFS/NTFS

Disk /dev/sdb: 2074 MB, 2074083328 bytes
64 heads, 32 sectors/track, 1978 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1978     2025455+   6  FAT16

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

cat /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

```

---

### Post by unutbu on 2008-03-16
Since the drive is external and is an NTFS, the device must be /dev/sdc1.
Now you need to choose where you want the external drive to be mounted.
Below, for the sake of concreteness, I call the mount point /media/seagate. Feel free to change it to whatever you want.

So in a terminal window, type:
```

sudo mkdir /media/seagate
sudo echo "/dev/sdc1 /media/seagate ntfs-3g defaults 0 0" >> /etc/fstab

```

To test that this works, then type
```

umount /dev/sdc1
mount /media/seagate

```

The drive should then be accessible at /media/seagate. After you reboot you should not have to type anything. The drive should be automatically available at /media/seagate.

---

### Post by enfeiris on 2008-03-16
After typing sudo echo "/dev/sdc1 /media/seagate ntfs-3g defaults 0 0" >> /etc/fstab, I got the following message:

bash: /etc/fstab: Permission denied

What should I do about this?

---

### Post by enfeiris on 2008-03-17
I hope I'm allowed to **bump**... if not, sorry!

---

### Post by unutbu on 2008-03-17
Try 
```

gksudo gedit /etc/fstab

```

Go to the end of the file and add this line:
```

/dev/sdc1 /media/seagate ntfs-3g defaults 0 0

```

Save and exit.

---

### Post by unutbu on 2008-03-17
If that does not work, please post output to

```

ls -l /etc/fstab

```

---

### Post by enfeiris on 2008-03-17
Still in read-only mode.

Output to "ls -l /etc/fstab" below...

-rw-r--r-- 1 root root 709 2008-03-17 10:48 /etc/fstab

---

### Post by enfeiris on 2008-03-17
I solved the problem using ntfs-config, which I downloaded with the following command:

```
sudo apt-get install ntfs-config
```

From there, it was pretty much self-explanatory.

Thanks for the help!:)

---

