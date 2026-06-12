---
title: "upgrading gspca for  Microsoft LifeCam VX-3000"
date: 2009-11-25
forum: Hardware
---

### Post by WithLinux on 2009-11-25
Here's some of my system information:```
#uname -a
Linux shrek 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

#lsusb
Bus 002 Device 002: ID 045e:00f5 Microsoft Corp.

#lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy


```So here's the problem.

Had my webcam working before but the picture quality was very very poor.  Snooped around in the forums and landed on this thread [http://ubuntuforums.org/showthread.php?t=885795&highlight=vx3000](http://ubuntuforums.org/showthread.php?t=885795&highlight=vx3000).  Sounds like many were able to get their webcam working with good quality but with newer versions of ubuntu. But went ahead and test it on my system grabbed the most recent drivers here [http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/%7Ejfrancois/gspca/") which was linked from the mentioned tread.  Did the usual make, make install and everything seemed to work out well.  I went ahead and restarted my system and 'lsmod' showed the module running.  I then tried running my webcam app but said it was an unsupported device.  I checked for /dev/video0 and that was fine.  I tried the suggested ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so [appNameHere]

``` without any luck.  The file does not exist for me, i'm guessing it has something to do with my version of ubuntu.

Disappointed i tried tried remove the module by going into lib/modules/`uname -r`/ and remove all traces of the module.  Then I tried building the old module that worked for me found here: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz).  When i tried to load the module i get this ```
#sudo modprobe gspca
FATAL: Error inserting gspca (/lib/modules/2.6.24-21-generic/kernel/drivers/usb/media/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```dmesg gives me:
```
#dmesg |tail
[ 9362.490031] gspca: Unknown symbol video_devdata
[ 9362.490282] gspca: Unknown symbol video_unregister_device
[ 9362.490381] gspca: Unknown symbol video_device_alloc
[ 9362.490428] gspca: Unknown symbol video_register_device
[ 9362.490593] gspca: Unknown symbol video_usercopy
[ 9362.490640] gspca: Unknown symbol video_device_release

```After a days of searching I just want to get my webcam working again.  I don't care if it is ugly.  It would be nice if I could fix that problem, but the bigger issue is it does not work anymore.

Also, just to provide as much information as I can...I did try to upgrade my kernel a while back with little to no success.  To be honest I don't know if it actually worked or not.  I followed some instructions online but I cant recall where.  I just know i was trying to upgrade the kernel in hopes to fix the same webcam problem.  So it might be possible that my symlinks links are wrong somewhere pointing to the wrong kernel source.  This might be useful```
 #ls -l /usr/src/
total 58396
-rw-r--r--  1 root root   153525 2007-10-29 15:57 gspca.tar.bz2
lrwxrwxrwx  1 root src        21 2009-11-25 00:03 linux -> /usr/src/linux-2.6.30
drwxr-xr-x 22 root root     4096 2009-11-25 00:05 linux-2.6.30
-rw-r--r--  1 root src  59435895 2009-06-09 20:22 linux-2.6.30.tar.bz2
drwxr-xr-x 20 root root     4096 2008-04-22 10:54 linux-headers-2.6.24-16
drwxr-xr-x  6 root root     4096 2008-04-22 10:54 linux-headers-2.6.24-16-generic
drwxr-xr-x 20 root root     4096 2008-11-06 00:45 linux-headers-2.6.24-19
drwxr-xr-x  6 root root     4096 2008-10-17 17:54 linux-headers-2.6.24-19-generic
drwxr-xr-x 20 root root     4096 2008-11-06 18:23 linux-headers-2.6.24-21
drwxr-xr-x  6 root root     4096 2009-11-24 23:55 linux-headers-2.6.24-21-generic
drwxr-sr-x  2 root src      4096 2009-08-24 22:56 oldpackages
-rw-r--r--  1 root src     92005 2009-08-16 14:22 patch-2.6.30.5.bz2
drwxr-sr-x  4 root src      4096 2009-08-24 00:24 trunk

```Did my best to elaborate my problem and explain how I got here.  Hopefully this is just some small problem I missed.  I know if all else fails I can do a fresh install of the latest release and it should fix the problem or get a better supported webcam but i really want to fix this problem.  For two reasons: one to get a better understanding of linux and secondly cuz it use to work! :P

Let me know if you need anymore information about my setup

Any ideas?

---

### Post by WithLinux on 2009-11-26
Still working on this without any luck.  No ideas from the community?

---

