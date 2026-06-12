---
title: "Error formatting external Maxtor usb hard drive"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by Stoffer on 2008-04-01
I've formatted this hard drive successfully in the past as ext2, but I can't seem to do it again.  mke2fs apparently worked, but it took 24 hours (80GB hdd) and resulted in ubuntu thinking it was 2TB large.  

So I tried again with gparted, which never works, and it came up as "unallocated space".  So I told it to format with ext2 and it gave me the following error:

```
GParted 0.3.3

Libparted 1.7.1

Create Primary Partition #1 (ext2, 74.53 GiB) on /dev/sda  03:16    ( ERROR )
     	
create empty partition  02:14    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 156296384
size: 156296322 (74.53 GiB)
set partitiontype on /dev/sda1  01:02    ( SUCCES )
     	
new partitiontype: ext2
create new ext2 filesystem  00:00    ( ERROR )
     	
mkfs.ext2 /dev/sda1
     	
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```

Any ideas?

---

### Post by fela on 2008-04-02
i've learnt from experience that gui tools can be problematic. heres a howto for reformatting your disk as ext3 using cfdisk ([COLOR="Red"]**REMEMBER TO REPLACE /dev/sda OR /dev/sda1 WITH THE APPROPRIATE DEVICE, OR YOU WILL CLOBBER THE WRONG FILESYSTEM AND LOSE ALL DATA ON THAT DISK**[/COLOR]), but here goes: ```
 sudo -s
``` ```
cfdisk /dev/sda
``` now when black screen comes up press 'n', select 'primary', press enter at default size. you should have one partition with type 'Linux' and size as big as the HDD. If that is correct, go ahead and press 'W' (with shift). When it's finished writing partition table, press 'q' to quit cfdisk. Now, when the terminal prompt comes up again, type ```
umount /dev/sda1
``` to make sure it's unmounted (and no, that's not a typo it really is 'umount'), then ```
mkfs -t ext3 /dev/sda1
``` to make the filesystem. This may take a while, but once it's finished, type ```
mkdir /mnt/external_hd && mount -t ext3 /dev/sda1 /mnt/external_hd
``` now navigate (using nautilus) to /mnt/external_hd and you should be able to access the hdd. (next time you plug the disk in, it should automount at /media/disk, and come up on the desktop)

---

