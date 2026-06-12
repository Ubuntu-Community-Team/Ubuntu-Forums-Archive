---
title: "Non-existant cdrom2 under places on panel"
date: 2010-01-03
forum: Hardware
---

### Post by Apv507 on 2010-01-03
I just installed 9.10, the look and speed is wonderful, but this is my second installation of karmic. My first installation right after its release kind of turned me off for several audio and other minor reasons... Long story short Super OS released its 9.10 version and I love it, except for one annoying thing: Under places it says I have a cdrom2 drive. I'm on a laptop (HP pavilion dv8000) with only one drive, any ideas on how I make this imaginary drive disappear? When the icon is clicked on I get the following error message: 

Unable to mount cdrom2
mount: special device /dev/scd1 does not exist

Any ideas? Thanks!

---

### Post by plucky on 2010-01-03
From a terminal window

What does ```
cat /etc/fstab
``` show you?

---

### Post by Apv507 on 2010-01-03
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5fbe4a2c-b15e-4909-8006-eb0e2cc5dbf0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=b38ab9c3-a6eb-43f9-b891-a04d802e1128 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
andrew@Apv-Laptop:~$ 




So should i delete /dev/scd1 and /media/cdrom2 using nautilus under root?

---

### Post by plucky on 2010-01-04
> So should i delete /dev/scd1 and /media/cdrom2 using nautilus under root? 

Where is the entry for the cdrom1 drive?

You could edit the /etc/fstab file so the line looks like ```
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
```

Then **reboot** and see if the other cdrom disappears and also test the actual cdrom drive works.

Good Luck

---

