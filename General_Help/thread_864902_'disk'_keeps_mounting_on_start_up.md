---
title: "'disk' keeps mounting on start up"
date: 2008-07-20
forum: General Help
---

### Post by fwaokda on 2008-07-20
The last two boot ups I've had a disk mount itself to my ubuntu. I only have one hard disk other than the one in my laptop.  The external hdd I have is 500gb and it also mounts.  This other disk mounts as 'disk' then the second time mounted as 'disk-1'.  I can't umount it by right-clicking on it and selecting unmount or I get this message.

        unable to unmount disk
        umount: /media/disk is not in the fstab (and you are not root)

I can unmount it if I do 'gksudo nautilius' and then get rid of it, however this is annoying to do on every startup.  If I right click the disk and select properties, most of the properities say unknown.  Although it says the size of the disk is 434.6gb. Also when you try to open the drive from the shortcut it gives this message.

        Couldn't display "/media/disk-1".
        There is no application installed for this file type

Thanks for anyone that responds I'll be checking back incase you need anymore information from me.

---

### Post by lisati on 2008-07-20
How are the partitions organized on your disks? Is there one partition on each of your disks, or is there more than one?

---

### Post by JagDragon on 2008-07-20
Check to see if it is in the fstab and being mounted. ```
gksu gedit /etc/fstab
```

---

### Post by fwaokda on 2008-07-20
> **lisati said:**
> How are the partitions organized on your disks? Is there one partition on each of your disks, or is there more than one?

I have one hdd in the laptop.  It is 160gb and is divided into 120gb and 40gb. Vista and Ubuntu respectively.  I then have a 500gb usb external hdd that is auto mounted every time I log on, which is a good thing.

> **JagDragon said:**
> Check to see if it is in the fstab and being mounted. ```
gksu gedit /etc/fstab
```

I don't really understand this one.  So, I'll try and answer as best I can.  I opened teh fstab and inside there is...

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4a251dee-ed1f-4d30-8d62-9318b00c317b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=54442342-81f8-4ba5-b48a-541431c2815f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
```

 Now the 'disk' that keeps mounting is not one I'm able to open or anything nor do I want to really.  I don't have a 434.6gb disk connect to the computer.  So I just want this disk to quick mounting itself, I don't know where it came from.  Thanks for your responses.

---

### Post by fwaokda on 2008-07-20
I ended up restarting this time without umounting the disk-1.  After doing that it seems to have fixed the problem. So if anyone is having the problem try restarting without 'sudo umounting' the drive. Good Luck -- I'll post anything else if it returns.


Also wanted to thank amenado on #ubuntu for helping me debug the situation! ;)  And of course you two for posting on here with some ideas. TY!

---

