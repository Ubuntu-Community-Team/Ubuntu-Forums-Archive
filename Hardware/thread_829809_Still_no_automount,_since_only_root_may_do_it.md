---
title: "Still no automount, since only root may do it?"
date: 2008-06-15
forum: Hardware
---

### Post by derfinsterling on 2008-06-15
I've got another question...

I'm still not able to automount my internal drives in Hardy.
I've got ntfs-config. I checked that it's activated.

I've followed the instructions found in various threads, for example this one:
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

My fstab file looks like this:
```
proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=16ebffc6-177b-45bc-8854-97dac66ee559 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=783fb0fc-fe45-4ee4-9394-977ebf78a5ae /home ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=9060DBEB60DBD5D6 /media/sda1 ntfs-3g defaults,locale=de_AT.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=D824F4CD24F4B01C /media/sda5 ntfs-3g defaults,locale=de_AT.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=f2958365-f243-4095-ab93-373cad2f02ee none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/cdrom /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```

The UUIDs are correct as well:
```
markus@scubuntu:~$ sudo vol_id -u /dev/sda1
9060DBEB60DBD5D6
markus@scubuntu:~$ sudo vol_id -u /dev/sda5
D824F4CD24F4B01C
```

Yet still, no automount.
The disks show up under Places... but if I click on them I get the error message:
"Unable to mount the volume 'Programme'."

The details are in German, but the gist is that only "root may mount /dev/sda5 to /media/sda5".

Any ideas beyond "make a clean install of Hardy"? (I've been getting this advice quite a lot lately ;-))

---

### Post by derfinsterling on 2008-06-19
Does nobody have an idea?

---

### Post by Odrodzona-Sarmacja on 2008-06-21
You may want to use in fstab
"nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000"
instead of
"defaults"
It should cure your problems.

---

