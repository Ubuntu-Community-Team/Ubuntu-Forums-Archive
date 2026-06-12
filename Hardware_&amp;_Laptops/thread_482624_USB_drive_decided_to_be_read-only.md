---
title: "USB drive decided to be read-only"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by Buster95 on 2007-06-23
I have been using a USB drive for some time now without mishap.
Then, yesterday, when I inserted it, it seemed to label itself as a music file and invoked Rhythmbox. The desktop icon even changed.
I now cannot save to it because I'm told that I'm trying to write to a read-only drive.
I tried changing it in file/edit/preferences, but it doesn't seem to change it.
How do I revert it to a normal read/write drive?
Thanks

---

### Post by ukripper on 2007-06-24
Is your USB  drive using ext3 or ntfs?

If it ntfs  then go to terminal and install following :

```
sudo apt-get install ntfs-config
```

Once installed just go to >  applications>system tools>ntfs configuration tool
and then open it and tick write for external drives.

Also can you post your output for following -
```
ls -al /media/usbdisk
```

---

### Post by Buster95 on 2007-06-28
> **ukripper said:**
> Is your USB  drive using ext3 or ntfs?

If it ntfs  then go to terminal and install following :

```
sudo apt-get install ntfs-config
```

Once installed just go to >  applications>system tools>ntfs configuration tool
and then open it and tick write for external drives.

Also can you post your output for following -
```
ls -al /media/usbdisk
```

Hello ukripper and thanks,
As far as I know it's ext3. This laptop doesn't carry any MS stuff at the moment.

dexter@dexim-laptop:~$ ls -al /media/usbdisk

ls: /media/usbdisk: No such file or directory

---

### Post by Buster95 on 2007-07-07
More on this problem:

I checked /etc/fstab (got the hint from the help file) and returned the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3f0666e5-64ba-4b2a-a8ad-01a00653fd7a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=02c62d0d-8167-419f-8df3-f98713d9d2e1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

It seems to be directing the usb stick to two different locations - /dev/sda6 which seems OK to me. sda6 is where my feisty hides. However, it also directs to /media/cdrom0.
Can't help but think that a usb data stick shouldn't be directing to a cdrm location.

Any advice?

In the meantime while I wait for pearls of forum wisdom, I'm going to comment out the bits I don't like to see if something good happens. Is this wise?

Cheers

---

