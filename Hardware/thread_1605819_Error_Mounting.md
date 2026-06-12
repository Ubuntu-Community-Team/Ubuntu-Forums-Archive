---
title: "Error Mounting"
date: 2010-10-25
forum: Hardware
---

### Post by raw157 on 2010-10-25
I have a 1 TB drive that is NTFS formated, and just has movies and pictures etc on it. When I try to open it mount it I get: 

Error mounting: mount exited with exit cod 12: Failed to read last sector.

How can I get into the drive?  I cannot reformat it, as I don't have anyway to back up all the data on it.. it was formated and is actively used in my Win7 partitions. 

Thanks,
Raw

---

### Post by sikander3786 on 2010-10-25
Did you ever use gparted to resize that partition?

Try ntfs fix and remount again.

```
sudo ntfsfix /dev/sdXY
```

Where sdXY is your drive identifier you can find it from

```
sudo fdisk -l
```

If it doesn't work, Please post the output of

```
cat /etc/fstab
```

and

```
sudo blkid
```

---

### Post by raw157 on 2010-10-27
---------fstab---------
When I run the "ntfsfix" one, it tells me "Failed to determine whether is mounted," but  I cannot mount is so... lol

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=59d33b3c-91aa-4d23-b5ac-5ebd9e3eddd5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=89a3fcf8-77ba-4045-9a75-a5791194b2eb /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b18d421e-80d9-4f39-b91d-b5ede63f583f none            swap    sw              0       0
  /dev/sdb1    /media/mynewdrive   ext3    defaults     0        2
robert@robert-MS-7388:~$ 



----------------blkid------

robert@robert-MS-7388:~$ sudo blkid
[sudo] password for robert: 
/dev/sda1: LABEL="New Volume" UUID="B608A76208A7207B" TYPE="ntfs" 
/dev/sdb1: LABEL="System Reserved" UUID="0C909CAD909C9F30" TYPE="ntfs" 
/dev/sdb2: LABEL="Big Movies/Music" UUID="D4949E3C949E20D2" TYPE="ntfs" 
/dev/sdc1: UUID="6498E00398DFD1A2" TYPE="ntfs" 
/dev/sdc5: UUID="b18d421e-80d9-4f39-b91d-b5ede63f583f" TYPE="swap" 
/dev/sdc6: UUID="59d33b3c-91aa-4d23-b5ac-5ebd9e3eddd5" TYPE="ext4" 
/dev/sdc7: UUID="89a3fcf8-77ba-4045-9a75-a5791194b2eb" TYPE="ext3" 
robert@robert-MS-7388:~$ 



Thanks again

---

### Post by raw157 on 2010-10-29
bump.

Anyone?

---

