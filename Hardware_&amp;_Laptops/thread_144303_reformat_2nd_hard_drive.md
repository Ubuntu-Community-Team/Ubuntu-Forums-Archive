---
title: "reformat 2nd hard drive"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by foobar on 2006-03-14
how can i reformat a 2nd hard drive with hoary

---

### Post by Sutekh on 2006-03-14
Have you tried running the Hoary Install CD yet?

Did it recognise your 2nd hard disc?  You should have the option of formatting the entire 2nd disc automatically.  You can of course setup the partitioning yourself too.

---

### Post by foobar on 2006-03-14
i have not tried the cd... how would i go about using it? 

i tried fdisk- deleted the old partition and created a new one. but when i try to mount it i get the following error-
```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Sutekh on 2006-03-14
In relation to the error, what format did you choose for the partition?  Does that correspond to the filesystem specified when you try and mount it?

For example a ext3 is mounted using ```
sudo mount /dev/hdb1 /media/hdb1 -t ext3
```
A FAT partition is mounted using
```
sudo mount /dev/hdb1 /media/hdb1 -t vfat
```


Hold on, I think I know what you are asking... you want to reformat your second hard-drive using Ubuntu?  (Or do you want to install Ubuntu on the second drive?)

To format the second drive in Ubuntu try using DiskDrake

[About DiskDrake]("http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake")

[Ubuntu Forums - Howto use DiskDrake]("http://www.ubuntuforums.org/showthread.php?t=114142")

There is also GParted, but I don't know how good the version is in the hoary repositories.

---

### Post by foobar on 2006-03-14
yes, i would like to reformat a 2nd hard drive with hoary

this is what the partition table looks like in fdisk-
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2434    19551073+  83  Linux

```
not really sure if its ext3 or what.

---

### Post by Sutekh on 2006-03-14
Looks ext3 to me

Try ```
sudo mount /dev/hdb1 /<path of your mount folder> -t ext3 -o defaults
```

---

### Post by foobar on 2006-03-14
that works... in fstab, i was using-
```
/dev/hdb1  /dmedia  ext3  defaults,umask=0000  0  0
```
but, now i am unable to create any folders/files unless im root. what do i need to change?

---

### Post by foobar on 2006-03-14
nm, re chmod'ing the dir worked...

thanks for your help Sutekh

---

### Post by Sutekh on 2006-03-14
Your welcome, glad its working now

Because ext3 is a Linux filesystem you don't need the umask setting, and chmod does work.  Unlike Windows filesystem which work the opposite.

---

