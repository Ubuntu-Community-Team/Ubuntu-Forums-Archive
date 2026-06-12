---
title: "Crashing after update"
date: 2008-07-16
forum: General Help
---

### Post by wgw on 2008-07-16
I just updated my gutsy (7.10) on my Thinkpad, 2.6.22-15-generic. Now my regular login hangs. I can login through recovery without any problem (that is why I can get on this forum!). I noticed in the last update that there was a linux image file (several megs) and new headers. That must be the problem. (I append the update log below.)

How do I track down the problem in the regular boot? When I turn off quiet in grub, I see that it hangs at "loading premount scripts". This discussion seems to indicate it might be a grub configuration problem: [http://ubuntuforums.org/showthread.php?t=860964&highlight=kernel+update](http://ubuntuforums.org/showthread.php?t=860964&highlight=kernel+update)

But it looks like the recovery and regular loading have the same grub configurations, which doesn't make sense if one works and the other doesn't. I don't know if grub is set properly because I don't understand the relation between the fdisk listing (see below) and the hd0,5 setting. All the grub entries say the same thing for the root option, hd0,5: 

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro splash
initrd		/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.22-15-generic root=UUID=1121e7a8-7dbc-4c3d-b71e-ae9323cf93fb ro single
initrd		/initrd.img-2.6.22-15-generic

My boot partition is sda6, so maybe that hd0,5 is accurate (counting from zero for hd0; from 1 for sda). 

Any suggestions on how to track the regular (defective) boot? 

Thanks!




bill@bill-laptop:~$ fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf15d99c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2664    21398548+   7  HPFS/NTFS
/dev/sda2            9169        9729     4505760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            2665        9168    52243380    5  Extended
/dev/sda5            2665        2924     2088418+  82  Linux swap / Solaris
/dev/sda6            2925        3611     5518296   83  Linux
/dev/sda7            6268        9168    23302251   83  Linux
/dev/sda8            3612        6267    21334288+  83  Linux

Partition table entries are not in disk order




2008-07-15 16:46:19 startup archives unpack
2008-07-15 16:46:39 upgrade linux-image-2.6.22-15-generic 2.6.22-15.54 2.6.22-15.56
2008-07-15 16:46:39 status half-configured linux-image-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:46:39 status unpacked linux-image-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:46:39 status half-installed linux-image-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:46:49 status half-installed linux-image-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:46:52 status unpacked linux-image-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:46:54 status unpacked linux-image-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:46:54 upgrade libpcre3 7.4-0ubuntu0.7.10.2 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:54 status half-configured libpcre3 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status unpacked libpcre3 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status half-installed libpcre3 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status half-installed libpcre3 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status unpacked libpcre3 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:54 status unpacked libpcre3 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:54 upgrade libpcrecpp0 7.4-0ubuntu0.7.10.2 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:54 status half-configured libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:54 status half-installed libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:55 status half-installed libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-07-15 16:46:55 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:55 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.3
2008-07-15 16:46:55 upgrade linux-headers-2.6.22-15 2.6.22-15.54 2.6.22-15.56
2008-07-15 16:46:55 status half-configured linux-headers-2.6.22-15 2.6.22-15.54
2008-07-15 16:46:55 status unpacked linux-headers-2.6.22-15 2.6.22-15.54
2008-07-15 16:46:55 status half-installed linux-headers-2.6.22-15 2.6.22-15.54
2008-07-15 16:46:59 status half-installed linux-headers-2.6.22-15 2.6.22-15.54
2008-07-15 16:47:00 status unpacked linux-headers-2.6.22-15 2.6.22-15.56
2008-07-15 16:47:01 status unpacked linux-headers-2.6.22-15 2.6.22-15.56
2008-07-15 16:47:01 upgrade linux-headers-2.6.22-15-generic 2.6.22-15.54 2.6.22-15.56
2008-07-15 16:47:01 status half-configured linux-headers-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:47:01 status unpacked linux-headers-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:47:01 status half-installed linux-headers-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:47:02 status half-installed linux-headers-2.6.22-15-generic 2.6.22-15.54
2008-07-15 16:47:03 status unpacked linux-headers-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:03 status unpacked linux-headers-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:03 upgrade linux-libc-dev 2.6.22-15.54 2.6.22-15.56
2008-07-15 16:47:03 status half-configured linux-libc-dev 2.6.22-15.54
2008-07-15 16:47:03 status unpacked linux-libc-dev 2.6.22-15.54
2008-07-15 16:47:03 status half-installed linux-libc-dev 2.6.22-15.54
2008-07-15 16:47:03 status half-installed linux-libc-dev 2.6.22-15.54
2008-07-15 16:47:04 status unpacked linux-libc-dev 2.6.22-15.56
2008-07-15 16:47:04 status unpacked linux-libc-dev 2.6.22-15.56
2008-07-15 16:47:05 startup packages configure
2008-07-15 16:47:05 configure linux-image-2.6.22-15-generic 2.6.22-15.56 2.6.22-15.56
2008-07-15 16:47:05 status unpacked linux-image-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:05 status half-configured linux-image-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:27 status installed linux-image-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:27 configure libpcre3 7.4-0ubuntu0.7.10.3 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status unpacked libpcre3 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status half-configured libpcre3 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status installed libpcre3 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status triggers-pending libc6 2.6.1-1ubuntu10
2008-07-15 16:47:27 configure libpcrecpp0 7.4-0ubuntu0.7.10.3 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status half-configured libpcrecpp0 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 status installed libpcrecpp0 7.4-0ubuntu0.7.10.3
2008-07-15 16:47:27 configure linux-headers-2.6.22-15 2.6.22-15.56 2.6.22-15.56
2008-07-15 16:47:27 status unpacked linux-headers-2.6.22-15 2.6.22-15.56
2008-07-15 16:47:27 status half-configured linux-headers-2.6.22-15 2.6.22-15.56
2008-07-15 16:47:27 status installed linux-headers-2.6.22-15 2.6.22-15.56
2008-07-15 16:47:27 configure linux-headers-2.6.22-15-generic 2.6.22-15.56 2.6.22-15.56
2008-07-15 16:47:27 status unpacked linux-headers-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:27 status half-configured linux-headers-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:27 status installed linux-headers-2.6.22-15-generic 2.6.22-15.56
2008-07-15 16:47:27 configure linux-libc-dev 2.6.22-15.56 2.6.22-15.56
2008-07-15 16:47:27 status unpacked linux-libc-dev 2.6.22-15.56
2008-07-15 16:47:27 status half-configured linux-libc-dev 2.6.22-15.56
2008-07-15 16:47:27 status installed linux-libc-dev 2.6.22-15.56
2008-07-15 16:47:27 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-07-15 16:47:27 status half-configured libc6 2.6.1-1ubuntu10
2008-07-15 16:47:44 status installed libc6 2.6.1-1ubuntu10

---

### Post by wgw on 2008-07-21
I found the solution: it was a corrupt swap file partition. This thread discusses the problem: [http://ubuntuforums.org/showthread.php?t=346157](http://ubuntuforums.org/showthread.php?t=346157).

---

