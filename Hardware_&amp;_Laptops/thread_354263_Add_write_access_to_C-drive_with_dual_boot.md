---
title: "Add write access to C-drive with dual boot"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by Mets on 2007-02-05
I dual-boot Ubuntu and Windows XP, and I'm trying to configure Ubuntu to allow me to write to my much larger Windows partition.  Currently, Ubuntu will automatically detect my other partitions and mount them, giving me read-only access.  I'd like to make that full write access.

I've read the following setup guide
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

They say that I should make a /media/windows folder and then append 
> /dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0.

I did sudo fdisk -l and saw that my C:\ is located at /dev/hdc2, just for reference while reading this post.  I appended the appropriate line, but the process did not work.  Perhaps that is because I already have an entry in /etc/fstab for hdc2 telling Ubuntu what to do with it upon boot?  Here is what it says in my file.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3 -- converted during upgrade to edgy
UUID=21d177d4-0dbb-4289-b142-0e7faa70701a / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=07D3-0609 /media/hdc1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdc2 -- converted during upgrade to edgy
UUID=4E90862B90861A1B /media/hdc2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc4 -- converted during upgrade to edgy
UUID=d3c8723b-ac22-42cb-9de6-210ae5f89ecb none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


I tried changing ntfs to ntfs-3g here, but that didn't work either.  I also tried using /media/windows and /media/hdc2.  No luck.  Can anybody tell me what my fstab file should look like, and how many entries for hdc2 I should have.  Thanks.

---

### Post by logos34 on 2007-02-05
Yes, you need to take out the original line
> # /dev/hdc2 -- converted during upgrade to edgy
UUID=4E90862B90861A1B /media/hdc2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

There should not be a hash ('#') mark in front of your new line.

You might also get ntfs-config...it will automatically convert your fstab entry and allows you to switch between read-only and r+w.

---

### Post by Mets on 2007-02-05
sweet program thanks, works great.

---

