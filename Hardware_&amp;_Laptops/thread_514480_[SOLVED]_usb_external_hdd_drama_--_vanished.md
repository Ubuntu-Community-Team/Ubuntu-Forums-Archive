---
title: "[SOLVED] usb external hdd drama -- vanished"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by robzbd on 2007-07-31
Hi, 

I read through a few posts but nothing seems to work. It probably is something little like a lock file, etc.. I have an external USB hdd that normally is recognized and mounted on startup, and I've had issues with it before from rough shutdowns (HAL mainly -- but that was simple enough to fix). 

Anyway, everything was normal until I decided to test out Mint, so I booted from the live CD and it hung up so I had to do a forced shutdown. When I tried to re-log into ubuntu again the external hdd is no longer visible. The weird part is, I had to unplug/replug the USB to the hdd or my keyboard/mouse wouldn't work. 

Heres some output if it helps:

**fstab**
```

[510][rob: ~]$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9ce0431-e908-4428-ada5-dd22b6954995 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=43f9a37b-f35a-4dcd-aca1-4fe5598521eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

**mount**
```

[511][rob: ~]$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=rob)

```

**fdisk**
```

[512][rob: ~]$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

```

**/dev/disk/uuid**
```

[513][rob: ~]$ ll /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root  80 2007-07-31 19:48 .
drwxr-xr-x 5 root root 100 2007-07-31 19:48 ..
lrwxrwxrwx 1 root root  10 2007-07-31 19:48 43f9a37b-f35a-4dcd-aca1-4fe5598521eb -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-07-31 19:48 e9ce0431-e908-4428-ada5-dd22b6954995 -> ../../sda1

```

**syslog**
```

[514][rob: ~]$ tail -f /var/log/syslog
Jul 31 19:50:47 hades kernel: [  128.311380] usb 5-4: device descriptor read/64, error -110
Jul 31 19:50:47 hades kernel: [  128.526932] usb 5-4: new high speed USB device using ehci_hcd and address 6
Jul 31 19:50:52 hades kernel: [  133.536353] usb 5-4: device descriptor read/8, error -110
Jul 31 19:50:57 hades kernel: [  138.645526] usb 5-4: device descriptor read/8, error -110
Jul 31 19:50:58 hades kernel: [  138.860970] usb 5-4: new high speed USB device using ehci_hcd and address 7
Jul 31 19:51:03 hades kernel: [  143.870424] usb 5-4: device descriptor read/8, error -110
Jul 31 19:51:08 hades kernel: [  148.979591] usb 5-4: device descriptor read/8, error -110

```

This is all new to me and I'm not really skilled with this sort of problem, any help is appreciated.

Thanks
-rob

---

### Post by merlinus on 2007-07-31
Have you tried to mount it manually?  This info may help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by robzbd on 2007-07-31
it doesnt look like its being picked up using 'sudo fdisk -l' so i'm not sure how to mount it

---

### Post by merlinus on 2007-07-31
Did you look at the link in my last post?  Is it recognized by windows (on this machine or some other)?

-merlin

---

### Post by meierfra on 2007-07-31
Try plugging it into a different USB port and see whether it makes a difference.

---

### Post by robzbd on 2007-07-31
Okay, problem solved. I think the key was the fact that if i booted with the drive plugged in the keyboard/mouse wouldn't work -- yet an unplug/replug of the USB drive solved that (still strange).

Anyway, I feel stupid because I didn't try the first thing that should have come to mind (read: unplug the power to the hdd and restart it).  It seems that did the trick.

@meierfra

I also tried a different USB port so you can take credit :)

@merlinus

I checked that link, but the system wasn't picking it up -- I guess the bad reboot had locked the drive itself. Thanks for the quick reply & help though.

-rob

---

