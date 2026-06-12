---
title: "Partition problems"
date: 2008-04-22
forum: Hardware
---

### Post by ack389 on 2008-04-22
Hi all, I've been having troubles with getting my partition to mount, get permissions to read/write and more.  I've been searching these forums for help and fear I have only made it worse.  The partition in question is /dev/sda3.  it is a 176.78gb partition on my 233gb internal HD.  I plan on using it to share media files between OSX and Ubuntu 7.10.  It was originally formatted as ext3 but I changed it to fat 32.  

here is my fstab


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ac6d7ef7-12c6-4708-8843-5bcc03ad24a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3F3C-1AF6  /media/EFI      System  Partition       vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=fa5d6eaa-c618-4307-8306-0705171dd7cd none            swap    sw              0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Now I know that the text isnt there for that partition, but it wasn't working before when it was there. 

Before when I typed "sudo mount -a" it said that line 8 is bad, and it still does even with the edited fstab.

I've been trying to do this for almost 4 days now and it is just driving me crazy.

I send thanks in advance as I know how helpful this community is.

---

### Post by Yellow Pasque on 2008-04-22
```
gksudo gedit /etc/fstab
```

Delete the "System Partition" in line 8 and change the group id to include all users (100), so it should look like:
```
UUID=3F3C-1AF6  /media/EFI   vfat   defaults,utf8,umask=007,gid=100 0 1
```

For /dev/sda3, use the above mount line for reference. To get the UUID:
```
sudo blkid
```

---

### Post by ack389 on 2008-04-22
When I type blkid it returns with
```

/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sda3: UUID="68e3be5b-fb90-4076-8a02-f91b7d15c114" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="ac6d7ef7-12c6-4708-8843-5bcc03ad24a6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="fa5d6eaa-c618-4307-8306-0705171dd7cd" 
alex@mbp:~$ 

```

However since sda3 is actually fat32,this seems wrong.  Also I feel weary to change system partition because I am on a mac and I have the rEFIt bootloader to dual boot mac and linux. Not trying to knock your response or anything. Thanks for the quick reply

---

### Post by Yellow Pasque on 2008-04-22
You're not changing the System partition. You're just fixing the mount line for it. The words, "System partition" should not be in the mount line.

Also, /dev/sda3 is ext3, not fat32. You must have done something wrong when trying to convert it.

---

### Post by ack389 on 2008-04-22
Alright, now I changed it to read 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ac6d7ef7-12c6-4708-8843-5bcc03ad24a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3F3C-1AF6  /media/EFI            vfat    defaults,utf8,umask=007,gid=100 0 1
# /dev/sda5
UUID=fa5d6eaa-c618-4307-8306-0705171dd7cd none            swap    sw              0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sda3
UUID=68e3be5b-fb90-4076-8a02-f91b7d15c114  /media/disk   ext3   defaults,utf8,umask=007,gid=100 0 1
```

I have read/write ability, but when I type mount -a it returns with
```
alex@mbp:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/68e3be5b-fb90-4076-8a02-f91b7d15c114 does not exist
alex@mbp:~$ 

```
Although I don't really think it matters much since it obviously does exist.  By the way, I changed it from ext3 to fat32 in gparted, and gparted recognizes it as fat 32 still.  thanks for the help man

---

