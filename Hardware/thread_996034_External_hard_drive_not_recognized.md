---
title: "External hard drive not recognized"
date: 2008-11-28
forum: Hardware
---

### Post by lode on 2008-11-28
Suddenly, without knowing if I even have/had anything to do with it -- I was browsing the drive in Thunar, but I don't remember doing anything distinctively strange --, my laptop (Lenovo Thinkpad T61) does no longer recognize my external hard drive (Lacie, 500 gigs, connected via USB).

Things I've tried to solve this problem (all my music is on there, so you could say it's a problem :)) so far:

- logging out of XFCE and logging in in KDE4, noticing KDE doesn't see the drive either
- powering off and on (i.e. cutting the power) of the external hard drive
- connecting the drive to my laptop via another USB port
- going to have something to eat
- cursing

So far none of these actions seem to have had any effect. The drive seems to be working properly (its little light is burning, I can feel/hear the drive spinning).

I don't even know where to start, so I guess posting on these forums isn't such bad idea ;)

This is my fdisk -l output, not knowing if it might or might not be of any help:

```
lode@sch294:~$ sudo fdisk -l
[sudo] password for lode: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
lode@sch294:~$ 

```

Thanks a bunch beforehand!

---

### Post by taurus on 2008-11-28
What filesystem is that external harddrive?  Power it up and plug it in and then post the output of this command from a terminal.

```
dmesg | tail
```

---

### Post by lode on 2008-11-28
I believe it's FAT32, but am not entirely sure.

dmesg | tail gives this:

```
[23550.513858] usb 5-2: new full speed USB device using uhci_hcd and address 6
[23550.639283] usb 5-2: device descriptor read/64, error -71
[23550.861982] usb 5-2: device descriptor read/64, error -71
[23551.077076] usb 5-2: new full speed USB device using uhci_hcd and address 7
[23551.198510] usb 5-2: device descriptor read/64, error -71
[23551.425184] usb 5-2: device descriptor read/64, error -71
[23551.641895] usb 5-2: new full speed USB device using uhci_hcd and address 8
[23552.048328] usb 5-2: device not accepting address 8, error -71
[23552.161178] usb 5-2: new full speed USB device using uhci_hcd and address 9
[23552.571032] usb 5-2: device not accepting address 9, error -71

```

---

### Post by lode on 2008-11-29
Apparently, rebooting my laptop fixed the problem, so I guess my problem is solved. Thanks for your help, taurus.

EDIT: Or not! Seconds after I posted this message, I lost contact with my drive again. This time, I wasn't browsing it or anything, just playing some music on it via MPD.

Somebody?

---

### Post by zymurgist on 2008-12-04
I've been battling this same issue. I have a 40GB ext3-formatted drive which worked fine for many years, until I got Ubuntu 8.04LTS. Now it has been hit or miss .. sometimes it will connect, sometimes it won't. Here's the most recent dmesg errors, which occurred in the middle of writing to it:

```

[ 3000.229399] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 3000.363017] usb 5-2: configuration #1 chosen from 1 choice
[ 3000.364775] usb-storage: device found at 5
[ 3000.364780] usb-storage: waiting for device to settle before scanning
[ 3005.352702] usb-storage: device scan complete
[ 4230.671291] usb 5-2: reset high speed USB device using ehci_hcd and address 5
[ 4230.786981] usb 5-2: device descriptor read/64, error -71
[ 4231.006430] usb 5-2: device descriptor read/64, error -71
[ 4231.221940] usb 5-2: reset high speed USB device using ehci_hcd and address 5
[ 4231.337601] usb 5-2: device descriptor read/64, error -71
[ 4231.557047] usb 5-2: device descriptor read/64, error -71
[ 4231.772622] usb 5-2: reset high speed USB device using ehci_hcd and address 5
[ 4232.179478] usb 5-2: device not accepting address 5, error -71
[ 4232.291199] usb 5-2: reset high speed USB device using ehci_hcd and address 5
[ 4232.698170] usb 5-2: device not accepting address 5, error -71
[ 4232.698212] usb 5-2: USB disconnect, address 5
[ 4232.834832] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 4232.946546] usb 5-2: device descriptor read/64, error -71
[ 4233.162013] usb 5-2: device descriptor read/64, error -71
[ 4233.385451] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 4233.509137] usb 5-2: device descriptor read/64, error -71
[ 4233.724611] usb 5-2: device descriptor read/64, error -71
[ 4233.940079] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 4234.347026] usb 5-2: device not accepting address 8, error -71
[ 4234.458823] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 4234.870788] usb 5-2: device not accepting address 9, error -71

```

There appears to be quite a few posts re: 8.04 and external (USB) drives not being recognized or eventually dropping out. But once the posts have tried all the obvious solutions, we're left hanging without anything more to go on.

So .. if anyone knows how to debug this, or where the relevant log files are, or someone can tell use what "device not accepting address x" means .. please help us .. or reformatting back to Windows XP may be our final resort.

---

