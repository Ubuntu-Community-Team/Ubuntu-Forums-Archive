---
title: "cant find extenal usb dvd drive"
date: 2008-08-23
forum: General Help
---

### Post by crashingsucks9 on 2008-08-23
i cant seem to get my external usb dvd drive to work with ubuntu, im not sure if it even recognizes it

thanks in advance

---

### Post by carolinason on 2008-08-23
You should be able to plug it in and Ubuntu detect it. You will need udev and hal working to do this.

When you plugin it in, the disk should mount on the desktop or at least in Nautiuls in the media directory.

```
ps -aux | grep -i hal
ps -aux | grep -i udev
```

---

### Post by crashingsucks9 on 2008-08-23
this is what i got when i put that in 

ben@squirrelnuts:~$ ps -aux | grep -i hal
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
111       4883  0.2  0.3   6324  4300 ?        Ss   16:02   0:00 /usr/sbin/hald
root      4948  0.0  0.0   3352  1164 ?        S    16:02   0:00 hald-runner
111       4966  0.0  0.0   2204   908 ?        S    16:02   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4980  0.0  0.0   3416  1152 ?        S    16:02   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event3 /dev/input/event4
root      4998  0.0  0.0   3420  1140 ?        S    16:02   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5001  0.0  0.0   3420  1144 ?        S    16:02   0:00 hald-addon-storage: polling /dev/scd1 (every 2 sec)
root      5587  0.0  0.0   3812   948 ?        Ss   16:02   0:00 /sbin/mount.ntfs-3g /dev/sdb1 /media/New Volume -o rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8
ben       5692  0.0  0.0   3004   776 pts/0    R+   16:04   0:00 grep -i hal
ben@squirrelnuts:~$ ps -aux | grep -i udev
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      2667  0.1  0.0   2412   960 ?        S<s  16:01   0:00 /sbin/udevd --daemon
ben       5694  0.0  0.0   3004   776 pts/0    R+   16:04   0:00 grep -i udev

---

### Post by carolinason on 2008-08-25
What is the output of
```
cat /etc/fstab
```
I'd like to check the file system table to see what is being mounted. it appears the drive /dev/sdb1 is being detected :)

---

### Post by JohnGalt131 on 2008-08-25
> **carolinason said:**
> What is the output of
```
cat /etc/fstab
```
I'd like to check the file system table to see what is being mounted. it appears the drive /dev/sdb1 is being detected :)

user@user-laptop:~/PDF$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90c6c1cd-b524-4419-91df-cf1c3ec60c31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ac5fc818-70ca-4bca-8fbc-990af5e30257 /home           ext3    relatime        0       2
# /dev/sda3
UUID=4c4bfd39-e371-4cff-b263-9859eff08787 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
UUID=3c09ffd8-d05f-42f3-a350-595c7d2a44b2 /home/user/Pictures ext3 users 0 2

---

### Post by JohnGalt131 on 2008-08-25
oops. I guess I should have mentioned, mine doesn't work either. I just realized I didn't start the post...It was conveniently started elsewhere.

---

