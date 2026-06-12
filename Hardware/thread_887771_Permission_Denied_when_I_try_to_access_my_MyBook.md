---
title: "Permission Denied when I try to access my MyBook"
date: 2008-08-12
forum: Hardware
---

### Post by julain124 on 2008-08-12
I connected my MyBook just now, and when I try to access it, it says permission denied.
Before I had this error, it would say that I had to add:

```
/dev/sdb1       /media/My Book ntfs-3g force 0 0
```

to **/etc/fstab.file**.

I did so, and now I am getting the error of Permission Denied.
how can I fix this?

---

### Post by dacorr on 2008-08-12
depends if it was removed from the Windows achine completly, if the lck file is stil in place it will prevent the mount without a force mount.

from terminal type

mount /dev/sdb1

and post what it says

---

### Post by julain124 on 2008-08-12
i did as was told. and this is what came up:

mount: can't find dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by dacorr on 2008-08-12
ok

try

sudo fdisk -l

to list the partitions

see what that says

---

### Post by julain124 on 2008-08-12
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000207286272 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee7f5cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

---

### Post by dacorr on 2008-08-12
ok no partition to mount.

I presume it is a USB HDD

so 

lsusb

to see if the device is detected

see what it says

---

### Post by theyranos on 2008-08-12
Are you trying to mount the drive as root?

If not, you may need to add ,user after the "force" on that fstab line.

---

### Post by dacorr on 2008-08-12
oh my bad missed the bottom bit

so its

mount /dev/sdb1

when you did this first tim did yyou place a / before dev?

---

### Post by julain124 on 2008-08-12
thats is correct. and when i did that, i got:

mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by dacorr on 2008-08-12
ok random idea

try

mkdir /home/username/Desktop/mybook

then

mount /dev/sdb1 /home/username/Desktop/mybook

try that first if it is an NTFS lock issue it will complain now

Dac

---

### Post by theyranos on 2008-08-12
Wait... is there actually a space in the fstab line where it says /media/My Book? If so, that might be the problem. I'm not sure how to escape spaces in fstab entries, but you might be better off anyway doing it in camelcase: /media/MyBook

---

### Post by julain124 on 2008-08-12
this is what came up:

Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /home/recklezz/Desktop/mybook -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /home/recklezz/Desktop/mybook ntfs-3g force 0 0


 i shall try again to add the line to fstab. I appreciate your help thanks! :)

---

### Post by julain124 on 2008-08-12
i tried adding it without the space, and i still get permissions denied. =[

---

### Post by dacorr on 2008-08-12
try this from terminal first

mount -t ntfs-3g /dev/sdb1 /home/recklezz/Desktop/mybook -o force

if it mounts

when done use

umount /dev/sdb1

then hopefully it will auto mount the next time like is should

if not then add it to the fstab

---

### Post by theyranos on 2008-08-12
does this give you the same error?
```

sudo mount -t ntfs-3g /dev/sdb1 /home/recklezz/Desktop/mybook -o force

```

---

### Post by dacorr on 2008-08-12
if you mount it as root then root will own the partion and you may not beable to write to it

---

### Post by julain124 on 2008-08-12
this fixed it: 
```
sudo mount -t ntfs-3g /dev/sdb1 /home/recklezz/Desktop/mybook -o force
```
Thank you sooo much!!! :) I really appreciate your help alot! :)

---

### Post by julain124 on 2008-08-12
> **dacorr said:**
> if you mount it as root then root will own the partion and you may not beable to write to it

I am able to write and transfer files to it. :)
Thanks again! +Thanks to both of you. :)

---

### Post by theyranos on 2008-08-12
For the future, it might be more convenient to have this in fstab so you don't have to type that big long thing again, and so you don't run into the permissions problems dacorr mentioned:
```

/dev/sdb1 /home/recklezz/Desktop/mybook ntfs-3g defaults,force,user 0 0

```

Then, next time you need access to these files, you should just be able to```
mount ~/Desktop/mybook
```

There's a good chance chance that if the sudo mount thing worked, then this will too.

---

