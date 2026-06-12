---
title: "I want Read Only Support for NTFS, like in Fiesty. How?"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by lolololololol on 2007-11-04
I have installed Kubuntu Gutsy. 

It has by default ntfs-3g installed which has Read/Write support.

I dont trust ntfs-3g (even though it is stable, dont want to take any chances), I want Read Only Support for ntfs, like in Fiesty. How?

And no i dont want to use ntfs3g-config to configure it to mount my ntfs drives in read only mode.

I have removed ntfs-3g using aptitude. 

Now how do i edit the /etc/fstab file to mount my ntfs drives in read only mode.

---

### Post by ddrichardson on 2007-11-04
```
/dev/hda1  /mnt/hda1 ntfs ro 0 0
```Is probably a good start.

---

### Post by lolololololol on 2007-11-04
> **ddrichardson said:**
> ```
/dev/hda1  /mnt/hda1 ntfs ro 0 0
```Is probably a good start.

It did not work, my fstab file is different format. :confused:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=1be854ce-b275-43c1-9f0a-cf211c1f0970 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=b00f92bb-687b-4787-993d-f9c801ccbb83 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=18E031FDE031E224 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=73e9fa0b-e734-4872-aea1-c87e31ed6283 /media/sda10    ext3    defaults        0       2
# /dev/sda5
UUID=CC040F9E9CB367BF /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=aff1ef4b-0ec1-45d2-8fd5-ee8231bfd5b3 /media/sda6     ext3    defaults        0       2
# /dev/sda8
UUID=9be83306-2fb2-4541-8cb4-7d5319c52253 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

:(

---

### Post by ddrichardson on 2007-11-04
Just add the ro option then.

---

### Post by mamlouk on 2007-11-04
> **ddrichardson said:**
> Just add the ro option then.
I'm guess that means that the line
```
# /dev/sda1
UUID=18E031FDE031E224 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```

should read
```
# /dev/sda1
UUID=18E031FDE031E224 /media/sda1     ntfs    defaults,umask=007,gid=46,ro 0       1

```

and the same would be for your sda5
```
# /dev/sda5
UUID=CC040F9E9CB367BF /media/sda5     ntfs    defaults,umask=007,gid=46,ro 0       1

```

---

### Post by ddrichardson on 2007-11-04
The umask value is also now fairly mute on a ro system.

---

