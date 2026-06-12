---
title: "None of my partitions are mountable anymore"
date: 2008-08-19
forum: General Help
---

### Post by Shampyon on 2008-08-19
I have two hard drives, neither removable. My main drive is divided into five partitions. The first is the Ubuntu partition; the other four are for data storage. The second drive is divided into three partitions, each for data.

I made a backup of /etc/fstab and tried editing the original to add all the partitions so they would be mounted at startup. Something went wrong, so I pasted the original back into /etc/ over the copy and restarted. Now none of my partitions except the main Ubuntu one will mount. The others say I have insufficient privileges, and I have a feeling I´ve messed something else up along the way that I just can´t remember. 

output of ***blkid***:
```
/dev/sda1: UUID="fc4c0820-4ed4-438c-939a-c3c72341f32b" TYPE="reiserfs" 
/dev/sda5: UUID="8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3" LABEL="sdb5" TYPE="reiserfs" 
/dev/sda6: UUID="9e3a4932-795c-41e4-b96a-4c33ba032c74" LABEL="sdb6" TYPE="reiserfs" 
/dev/sda7: UUID="e35621df-059d-4288-b99c-8917ba917848" LABEL="sdb7" TYPE="reiserfs" 
/dev/sda8: UUID="e6df3e16-1257-46a8-aa93-2718b84102a4" LABEL="sdb8" TYPE="reiserfs" 
/dev/sdb1: UUID="ef823bf7-7c22-4a40-a32c-da3e628ad8d4" TYPE="reiserfs" 
/dev/sdb2: UUID="90061adf-b9c3-4f97-ba7b-2efe8ffca164" TYPE="reiserfs" 
/dev/sdb3: UUID="8c80e9ff-b985-4069-9c31-c6d7f7561832" TYPE="reiserfs"
``` 

Output of ***fdisk -l***:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42ca42ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6080    48837568+  83  Linux
/dev/sda2            6081       30401   195358432+   f  W95 Ext'd (LBA)
/dev/sda5            6081       12160    48837568+  83  Linux
/dev/sda6           12161       18240    48837568+  83  Linux
/dev/sda7           18241       24320    48837568+  83  Linux
/dev/sda8           24321       30034    45897673+  83  Linux
/dev/sda9           30035       30401     2947896   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdec7dec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+  83  Linux
/dev/sdb2            6375       12748    51199155   83  Linux
/dev/sdb3           12749       19457    53890042+  83  Linux
```

Output of ***ls /dev/disk/by-uuid -alh***:
```
total 0
drwxr-xr-x 2 root root 220 2008-08-19 15:15 .
drwxr-xr-x 6 root root 120 2008-08-19 15:15 ..
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 6180b5f7-152f-4942-b253-02631555ae18 -> ../../sda9
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 8c80e9ff-b985-4069-9c31-c6d7f7561832 -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 90061adf-b9c3-4f97-ba7b-2efe8ffca164 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 9e3a4932-795c-41e4-b96a-4c33ba032c74 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 e35621df-059d-4288-b99c-8917ba917848 -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 e6df3e16-1257-46a8-aa93-2718b84102a4 -> ../../sda8
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 ef823bf7-7c22-4a40-a32c-da3e628ad8d4 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-08-19 15:15 fc4c0820-4ed4-438c-939a-c3c72341f32b -> ../../sda1
```

Contents of ***/etc/fsta***b:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc4c0820-4ed4-438c-939a-c3c72341f32b /               reiserfs notail,relatime 0       1
# /dev/sda9
UUID=6180b5f7-152f-4942-b253-02631555ae18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by cdtech on 2008-08-19
Not sure why, but my fstab "/" partition is set a little different than yours:
```
UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 / ext3 defaults,errors=remount-ro 0 1
```

Should be able to mount via command line anyway....

---

### Post by Shampyon on 2008-08-19
I can manually mount them, but this will be pretty time consuming when I have seven partitions to manually mount every time I boot up. Also, they don´t seem to be accessible through the *Places* menu or the side pane in Nautilus.

Is there some way to automatically regenerate the relevant files as though it were a fresh install, without actually having to reinstall Ubuntu? Something with the live CD perhaps?

---

### Post by cdtech on 2008-08-19
I think this bug might have something to do with your problem:
[https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736](https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736)

---

### Post by Shampyon on 2008-08-19
I don´t really understand the content of that link, it just goes way over my head. It seems to be something to do with ecryption, though. I haven´t tried to encrypt anything. It said something about deleting the file /var/run/pam_mount/$USER, but I don´t have a pam_mount folder in /var/run/.

Is there any way to use the live CD to just repairt/reinstall the fstab and/or mtab or whatever else is needed to make it recognise my partitions they way it did when I first did this fresh install yesterday?

---

