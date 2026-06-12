---
title: "grub will not work"
date: 2008-11-27
forum: General Help
---

### Post by melenor on 2008-11-27
All right i recently made my ubuntu partition bigger, but the grub no longer works following previous guides i did this
```

>sudo grub
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
grub> root (hd0)
root (hd0)
grub> setup (hd0,1)
setup (hd0,1)

Error 17: Cannot mount selected partition

```
 I have no idea how to fix this.
Thanks for any help.

---

### Post by dagnabit dang doohickey on 2008-11-27
You're using the root and setup commands with the arguments flipped. Try:

```
root (hd0,1)
setup (hd0)
```

---

### Post by meierfra. on 2008-11-27
Post the output of 

```
sudo fdisk -lu
```

What program did you use to resize Ubuntu?

What happens when you try to boot Ubuntu? Does the grub menu appear? (You might have to press "Esc" after the bios screen) Any error messages ?

> Error 17: Cannot mount selected partition

Do you get this error at boot up? Or at the "grub prompt" in the LiveCD?

---

### Post by meierfra. on 2008-11-27
> root (hd0,1)
setup (hd0)
+1. (I didn't noticed that you used "root (hd0)")

---

### Post by melenor on 2008-11-27
-I used gparted
-grub menu appears but says that the partition does not exsit

partition that ubuntu is on it /dev/sda3
I have followed what you said meierfra and will reboot right now.

---

### Post by melenor on 2008-11-27
just rebooted it says 
```
 
Boot from (hd1,1) ext3 
Error 15: File not found 
Press any key to continue.

```

---

### Post by meierfra. on 2008-11-27
Post the output of 

```
sudo fdisk -lu
```

and

```
sudo mount /dev/sda3 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by meierfra. on 2008-11-27
Try this:

At the grub menu at boot up, press "c".  Type

```
find /boot/grub/stage1
```
The output will be of the form (hdX,Y)

Press "Esc"  to get back the grub menu. Select Ubuntu and press "e". At the new screen press "e" again. Change the line to

```
root (hdX,Y)
```
(Use the numbers you got from  "find /boot/grub/stage1")

Press "enter" and then "b" to boot. If this lets you boot into Ubuntu, you still have the make the changes permanent. Open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Change 

"# groot=(hd?,?)" to "# groot=(hdX,Y)"

Save  the file. Back in the terminal

```
sudo update-grub
```

That should be it.

If this does not work, post the information I requested in my previous post. And also the output of the "find /boot/grub/stage1" command

---

### Post by melenor on 2008-11-27
sudo fdisk -lu
```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40d3549b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   111153734    55576836   83  Linux
/dev/sda3       111153735   490223474   189534870    5  Extended
/dev/sda5       112744170   490223474   188739652+   b  W95 FAT32
/dev/sda6       111153861   112744169      795154+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8055

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *          63  1465144064   732572001    7  HPFS/NTFS

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49262675

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             245     1999871      999813+   b  W95 FAT32

```
sudo mount /dev/sda3 /mnt
```

mount: you must specify the filesystem type

```

cat /mnt/boot/grub/menu.lst
```

cat: /mnt/boot/grub/menu.lst: No such file or directory

```

I will do that one right now and post results

EDIT: What line do i add the 
```
root (hdX,Y) 
```
-btw "find /boot/grub/stage1" returned "(hd1,1)

on the first line it has uuid and alot of numbers
then comes kernel that has the "root=UUID=" and numbers from first line

---

### Post by melenor on 2008-11-27
just replaceing the first line gives me an error however, I think that is because of the "root=UUID=78587026-b7b5-4943-a56d-d361f269fdb3" 
the line i replaced was 
"uuid 78587026-b7b5-4943-a56d-d361f269fdb3"

---

### Post by melenor on 2008-11-27
Duplicate Post

---

### Post by meierfra. on 2008-11-27
> I think that is because of the "root=UUID=78587026-b7b5-4943-a56d-d361f269fdb3" 
Yes, the UUID's changed since you resized your partition.


Do this:


```
sudo mount /dev/sda2 /mnt
sudo blkid  | grep sda2

```
The output will give you the correct UUID for your Ubuntu partition. Open fstab and menu.lst via 

```

gksudo gedit /mnt/etc/fstab  /mnt/boot/grub/menu.lst
```

and replace all the "UUID=78587026-b7b5-4943-a56d-d361f269fdb3" by the correct UUID.


Reboot and you should be all set.

---

### Post by melenor on 2008-11-27
do i do this from the grub menu or from the liveCD?

---

### Post by meierfra. on 2008-11-27
Live CD

---

### Post by melenor on 2008-11-28
it says that i must specify filesystem type. i tried ext3 but instead it just brought up alot of options.
Also are you sure that you do not mean /dev/sda3 instead of /dev/sda2.
/dev/sda2 - says linux
/dev/sda3 - says extended.

---

### Post by meierfra. on 2008-11-28
It really should be "sda2".

---

### Post by meierfra. on 2008-11-28
It seems there is something wrong with your Ubuntu partition. Post the output of

```
sudo mount -t ext3 /dev/sda2 /mnt
```

Also try  a file system check:

```
sudo umount /dev/sda2
sudo e2fsck -yv /dev/sda2 
```

(The first command will probably give you an error message, ignore that. I just want to make sure that the Ubuntu partition is unmounted when you run the files system check.)

---

### Post by melenor on 2008-11-28
Alright I was able to mount the drive and find the new UUID which is "78589026-b7b5-4943-d361f269fdb3" 
The filesystem check says clean. I am going to try the replace the UUID.

---

### Post by melenor on 2008-11-28
All right i tired replaceing the UUID but i still received the error. I am thinking about just trying to backup my peferences and just reinstalling it. If i cannot find an answer that is, because with the time that this has taken i could have reinstalled it already.

---

### Post by meierfra. on 2008-11-28
Since the grub menu appears, it really shouldn't be all that difficult to get Ubuntu to boot.

Please boot from the LiveCD and post the output of

```
sudo mount /dev/sda2 /mnt
sudo blkid 
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

I  also noticed that there is a problem with your partition table:

dev/sda5       112744170   490223474   188739652+   b W95FAT32
dev/sda6       111153861   112744169      795154+  82  Linux swap / Solaris

/dev/sda6    ends at  112744169  and /dev/sda5 start at  112744170. But there need to be at least 63 sectors between two logical partition. 

So you need to check out your partition table with  testdisk.  In the LiveCD, enable the "universe" repository in System > Admin > Software Sources,

Install testdisk and run testdisk via

```
sudo apt-get install testdisk
sudo apt-get
```

Select   "create log", select "/dev/sda" and "proceed", "Intel", "Analyze" (post this output). Then do "proceed", "Y" only if you have a Vista partition, hit enter and select "search!" so it does a deeper search (which will take a while). Please post the output of its results when it's done.

---

