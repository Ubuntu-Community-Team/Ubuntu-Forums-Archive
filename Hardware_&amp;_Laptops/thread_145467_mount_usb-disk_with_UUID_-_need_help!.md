---
title: "mount usb-disk with UUID - need help!"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by mogliii on 2006-03-16
Hi,
I have Kubuntu 5.10

I also posess two USB drives. For the entry in /etc/fstab I dont want to use /dev/sda* because its changing. Instead I want
```
UUID=**** /mountpoint ext3 options
```


I also found a page explaining it
[http://www.wlug.org.nz/PartitioningSuggestions]("http://www.wlug.org.nz/PartitioningSuggestions")

And there it is written:
> The partition UUID is **guaranteed to be universally unique**, and will always point to the same partition. UUIDs are supported on all (AddToMe: check this) filesystems linux supports, including swap and vfat.

So I checked the UUID of both harddrives and entered it in the fstab, but both were mounted to the same point. And then I found out, that both partitions have the same UUID.
```
blkid | grep 03138356-5e61-4ab3-b58e-27507ac41937
/dev/sda2: LABEL="M-USB-DATA" TYPE="ext2" UUID="03138356-5e61-4ab3-b58e-27507ac41937"
/dev/sdc2: LABEL="M2-USB-DATA" UUID="03138356-5e61-4ab3-b58e-27507ac41937" SEC_TYPE="ext2" TYPE="ext3"

```
The partitions dont have identical physical conditions. And the two FAT partitions have different UUID's
```
/dev/sda1               1          32      257008+   6  FAT16
/dev/sda2              33       19457   156031312+  83  Linux

/dev/sdc1               1          12       96358+   b  W95 FAT32
/dev/sdc2              13       30401   244099642+  83  Linux

```
How can this happen and how can I change the UUID? You can set it with pvcreate but I dont know this tool and in the man page I read too much about delete... 
 Can anyone help me?

---

### Post by mogliii on 2006-03-16
Hi,

I found a solution on a german site
[http://linuxwiki.org/UUID]("http://linuxwiki.org/UUID")

in short: to change ext2/3 UUID type
```
tune2fs -U 01234567-89ab-cdef-0123-456789abcdef
```

officially UUID is not supported on FAT, but for me it works... But I have no idea why.

---

### Post by DaBruGo on 2006-03-17
Hi, 

Did you use the UUID numbers in your menu.lst file for the GRUB bootloader. If so, what do your kernel config lines look like in the menu.lst file? What does your /etc/fstab file look like?

I am curious because I would like to label an external USB drive so the GRUB bootloader will know where to get the kernel when booting up, instead of having to make sure the drive always shows up as /dev/sda to the operating system at startup. 

I haven't been able to get the "root=LABEL=mylabel" option to work yet in the menu.lst file. (I believe the only two options available for this are either LABEL or UUID.) Maybe the UUID option will work for me?


Thanks again for posting your info!

DAVE

---

### Post by mogliii on 2006-03-19
Hi DaBruGo

as I use those usb-devices only for DATA and I dont need them at start up, I dont use UUID in the menu.lst

But it would be very interesting, if and how it works?!?

---

### Post by DaBruGo on 2006-03-20
[quote=mogliii]Hi DaBruGo
 
as I use those usb-devices only for DATA and I dont need them at start up, I dont use UUID in the menu.lst
 
But it would be very interesting, if and how it works?!?[/quote]
 
mogliii.
 
Thanks anyway. I have been trying for a week (on ubuntuforums and on google) to find a howto/tutorial on accomplishing this (with either LABEL or UUID).
 
 
( sigh :( )
DAVE

---

