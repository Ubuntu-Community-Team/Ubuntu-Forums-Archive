---
title: "partitioner deactivate and unmount options"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by doglover56 on 2009-01-25
Hello. I have a multiboot system with lots of partitions. I don't want to mount them all, and I set the mount point to the blank choice, but the installer seems not to like that choice even though it offers it and tries to force you to choose a mount point. 

In the XUbuntu 6.06.1 partitioner (refer to prior post to see why I am using this older version), right clicking on a drive offers options to unmount or deactivate a partition. I am guessing that is what I want, but neither google nor a ubuntu search nor the installation manual explain these. 

I have other OSes on computer, so I wanted to make sure that these options will not mess those up. 

Does anyone know or have know of documentation explaining what unmounting or deactivating partitions in the partitioner does to the current or prior installs, and how they differ?

Thanks,
doglover

---

### Post by taurus on 2009-01-25
Which partitions you don't want to mount at boot?

Open a terminal and post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by doglover56 on 2009-01-25
Here is fstab. I already know that I can edit fstab, which is what I did when I installed Ubuntu. I would like to try something different for installying Xubuntu, so the original question about unmount and deactivate still stands.
Thanks,
IMF


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda19
UUID=9dd517b0-6554-47df-b57a-eed08747721a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda20
UUID=72bec888-5e80-4ff7-b3a9-e1e6ddaf03ee /home           ext3    defaults        0       2
# /dev/hda1
# UUID=47BF-FBB1  /media/hda1     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda10
# UUID=BD11-9E6B  /media/hda10    vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda11
# UUID=FC17-8184  /media/hda11    vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda12
# UUID=7A23-4DE6  /media/hda12    vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda13
# UUID=3F05-E4A1  /media/hda13    vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda14
# UUID=E064C2AC64C2852E /media/hda14    ntfs    defaults,nls=utf8,umask=007,gid=46,ro 0       1
# /dev/hda15
# UUID=000000007F93E58A /media/hda15    ntfs    defaults,nls=utf8,umask=007,gid=46,ro 0       1
# /dev/hda16
# UUID=4661-BD8D  /media/hda16    vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda17
# UUID=FCF4EDADF4ED69FA /media/hda17    ntfs    defaults,nls=utf8,umask=007,gid=46,ro 0       1
# /dev/hda2
# UUID=36408DAB408D7283 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46,ro 0       1
# /dev/hda3
# UUID=3847-1DFB  /media/hda3     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda5
# UUID=3F05-CBE5  /media/hda5     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda6
# UUID=3F05-CE7F  /media/hda6     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda7
# UUID=3F05-DB47  /media/hda7     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda8
# UUID=3F05-DF4D  /media/hda8     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda9
# UUID=7E0B-BEBE  /media/hda9     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hdc2
# UUID=A4B3-127E  /media/hdc2     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hdc5
# UUID=3F37-F963  /media/hdc5     vfat    defaults,utf8,umask=007,gid=46,ro 0       1
# /dev/hda18
UUID=15d43a0a-eb4c-4910-aa3e-c21ac3575730 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

