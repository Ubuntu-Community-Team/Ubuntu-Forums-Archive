---
title: "Can't view files on 2nd drive"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Kittens on 2007-01-11
I mounted a 2nd hard drive so that I could transfer my old documents to my new Ubuntu system, but for some reason I am unable to view the files in the HD. I am assuming that this has something to do with Ubuntu reading the drive as a read-only (or something). I followed a step-by-step instructional how-to, but I believe I did something wrong.

Here is what I followed: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Please can someone assist?

P.S. Sorry if this is the wrong section.

---

### Post by meng on 2007-01-11
This has nothing to do with viewing as read-only. You need to tell us EXACTLY what you did and if you got any error messages.

---

### Post by Kittens on 2007-01-11
I followed the how-to on the page, replaced what I assumed was what was listed in the screen shots, and received no errors messages.

I went into the Terminal, copied each code I read that I was to enter, and finished. I don't remember seeing anything that looked like an error. I thought I had done everything well.

---

### Post by taurus on 2007-01-11
What's the output of these three commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Kittens on 2007-01-11
sudo fdisck -l :
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         775     5858968+   b  W95 FAT32
/dev/hdb2   *         776        5168    33211080    7  HPFS/NTFS
```

cat /etc/fstab :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
# /dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
# /dev/hda5
UUID=90262978-3be9-4d73-85ab-f7fb60b3e8fc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

df -h : 
```
Filesystem            Size  Used Avail Use% Mounted on
varrun                363M   84K  363M   1% /var/run
varlock               363M     0  363M   0% /var/lock
udev                   10M  104K  9.9M   2% /dev
devshm                363M     0  363M   0% /dev/shm
lrm                   363M   18M  346M   5% /lib/modules/2.6.17-10-generic/volatile
```

---

### Post by meng on 2007-01-11
In your /etc/fstab:
The line that starts with # /dev/hdb1 ... remove the # from the beginning of that line.
The line that starts with # /dev/hda1 ... remove the # from the beginning AND change hda1 to hdb2

In order to edit your fstab, you need to open a text editor with superuser privileges, like this:
sudo nano -B /etc/fstab

(ctrl-x to exit and save changes)

NOW you need to make sure there are folders named /windows and /fat_files (actually, I would personally recommend you use /media/windows and /media/fat_files instead, which would require you make the necessary changes to your /etc/fstab file. But Linux is all about choice, do whatever suits you.) If you haven't already created the folders, you need to do this:
sudo mkdir /windows (or /media/windows)
sudo mkdir /fat_files (or /media/fat_files)

Now do this:
sudo mount -a

and tell us how it goes.

---

### Post by Kittens on 2007-01-11
Problem solved. I can now view all my old documents. Thank you very much!

---

