---
title: "Not Privileged to Mount Volumes"
date: 2008-08-31
forum: General Help
---

### Post by Hawk__0 on 2008-08-31
This randomly started today.  I cannot mount anything. My DVD-RW, my external hard drive... I get the error "You are not privileged to mount this volume"

---

### Post by mb_webguy on 2008-08-31
Post the output of "cat /etc/fstab".

---

### Post by Hawk__0 on 2008-08-31
```
cat steve@steve-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0146284-521c-49d2-9254-ff57888d07bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4b1ab144-594e-4e84-b604-e756b7589c88 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/home		auto		noatime	        0        1
/dev/sdc1	/media/vault	auto		noatime		0	1

steve@steve-desktop:~$ 

```

---

### Post by Hawk__0 on 2008-08-31
bump

---

### Post by Sycron on 2008-08-31
How are you mounting drives ?

---

### Post by Hawk__0 on 2008-08-31
just by clicking on them or when they autorun.  it used to work

---

### Post by firfin on 2008-08-31
Same here. Cant automount my ntfs partitions from nautilus anymore (.places / sidebar)
Could be related to [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119302](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119302) maybe?

---

### Post by ARhere on 2008-08-31
After plugging in the drive, goto the "Places" drop down menu and open "Computer" and see if your device is there.  If so, try opening it as the OS will auto mount if possible.

If not, then try, ```
mkdir ~/Desktop/mydisk
sudo mount /dev/<device> ~/Desktop/mydisk
``` and the automounter sometimes will be invoked by this and you will see two mount points; the one you just created and the automount one.

This just happened to me today and after that, everything was ok.
-AR

---

### Post by Hawk__0 on 2008-09-01
With that yes, I can mount the volume (which is obvious because I'm mounting it as root).  But after unmounting it I cannot remount it as my regular user.  I also modified my fstab and get more information on my error:
[IMG]http://img296.imageshack.us/img296/4240/erroreh0.jpg[/IMG]

Edit: 
I fixed it magically somehow....

I did what the error said.. kind of.. I reinstalled ntfs-3g (apt-get remove, then install) then I deleted my Vault's entry from fstab and now BOTH my vault AND DVD-RW mount fine!

Not really sure why my dvd-rw started to work all a sudden but its all good now :D

Thanks for the help!

---

### Post by ARhere on 2008-09-01
Glad it's fixed.

Please mark post as SOLVED if you are happy.

-AR

---

### Post by Warner White on 2008-11-09
I succeeded in mounting the volume using the mydisk method. But I find that it goes unmounted when I reboot after shutting down.

How can I make the mounting permanent?

Boy, am I glad you guys exist!

WW

---

