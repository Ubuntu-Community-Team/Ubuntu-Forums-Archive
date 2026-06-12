---
title: "invalid encoding and messed up partition table"
date: 2008-09-01
forum: General Help
---

### Post by albesan on 2008-09-01
hello team,

I'm not sure how it happened but I've lost a partition and can't find it.

 fdisk -l tells me that it is there (/dev/sda8) and that it is a linux partition.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7226    57994650    7  HPFS/NTFS
/dev/sda3            7227       14593    59175427+   f  W95 Ext'd (LBA)
/dev/sda5           14332       14593     2104483+  dd  Unknown
/dev/sda6           10661       13914    26137723+  83  Linux
/dev/sda7           14175       14331     1261071   82  Linux swap / Solaris
/dev/sda8            7227       10404    25527222   83  Linux
/dev/sda9           10405       10660     2056288+  82  Linux swap / Solaris
/dev/sda10          13915       14174     2088418+   b  W95 FAT32

Gparted sees it too it displays it as having the right size but can't mount it.
When I mount it from the terminal using:

 sudo mount /dev/sda8 /home/albesan/Desktop/backup/

All I can see in it is what is on the screenshot attached and the actual partition being mounted is sda1 

Any ideas anyone?

Thanks

a.

---

### Post by prshah on 2008-09-01
> **albesan said:**
> 
 fdisk -l tells me that it is there (/dev/sda8) and that it is a linux partition.
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7226    57994650    7  HPFS/NTFS
/dev/sda3            7227       14593    59175427+   f  W95 Ext'd (LBA)
/dev/sda8            7227       10404    25527222   83  Linux
/dev/sda9           10405       10660     2056288+  82  Linux swap / Solaris
/dev/sda6           10661       13914    26137723+  83  Linux
/dev/sda10          13915       14174     2088418+   b  W95 FAT32
/dev/sda7           14175       14331     1261071   82  Linux swap / Solaris
/dev/sda5           14332       14593     2104483+  dd  Unknown

```


fdisk table rearranged for clarity.

Can you post the outputs to the following commands```
sudo blkid
mount
cat /etc/fstab
```

All three outputs above seem to play a role in this. With this, it will probably be easy to solve.

---

### Post by albesan on 2008-09-02
hey,
thanks for your reply.

here is the output:

blkid

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-061A" TYPE="vfat" 
/dev/sda2: UUID="CCBC3344BC33287A" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="07D7-061A" TYPE="vfat" 
/dev/sda6: UUID="49e95b00-8ffb-47b0-9fa0-d0ea6da472a4" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="f42208a7-89f2-4c88-9c08-c2b410ab4382" 
/dev/sda8: UUID="6cb640b5-7a7d-415e-bb8c-98d6b7160b15" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="8b14f49a-c12b-41cb-957a-b1297d7cc093" 
/dev/sda10: UUID="48AC-61CC" TYPE="vfat" 

mount

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/albesan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=albesan)

cat /etc/fstab

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=49e95b00-8ffb-47b0-9fa0-d0ea6da472a4 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
#UUID=6cb640b5-7a7d-415e-bb8c-98d6b7160b15 /home/albesan/Desktop/backup ext3 #defaults,relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=f42208a7-89f2-4c88-9c08-c2b410ab4382 none swap sw 0 0
# Entry for /dev/sdc2 :
UUID=6cb640b5-7a7d-415e-bb8c-98d6b7160b15 /media ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=8b14f49a-c12b-41cb-957a-b1297d7cc093 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda10 /media/sda10 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0

thanks again.

a.

---

### Post by prshah on 2008-09-02
> **albesan said:**
> 
# Entry for /dev/sda8 :
#UUID=6cb640b5-7a7d-415e-bb8c-98d6b7160b15 /home/albesan/Desktop/backup 

Why is the entry for /dev/sda8 commented out?

---

### Post by albesan on 2008-09-02
hey PRShah,

I commented out that entry because it wasn't working anyway.

I managed to fix it. To be honest not very sure how.
I think during an update a new version of grub was installed and grub got messed up somehow.
After quite a bit of trial and error and using unetbooting-suergrub I managed to boot from the partition and and fix things up.

Thanks again for your replies, apreciate it

a.

---

### Post by albesan on 2008-09-02
deleted----double post

---

