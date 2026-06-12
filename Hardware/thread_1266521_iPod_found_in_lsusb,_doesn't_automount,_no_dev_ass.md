---
title: "iPod found in lsusb, doesn't automount, no /dev assignment"
date: 2009-09-14
forum: Hardware
---

### Post by Literati on 2009-09-14
Hi all, when I plug in my iPod I get:

> dmesg wrote:```
[ 4519.208046] usb 1-4: new high speed USB device using ehci_hcd and address 8
[ 4519.377226] usb 1-4: configuration #1 chosen from 2 choices

```

and if I use lsusb I can see my iPod as:

> lsusb wrote: ```
Bus 001 Device 008: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

But if I look for it with mount I can't find it...

> mount wrote: ```
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alain/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alain)

```

Nor is it in my fstab or anything. So I'm looking for a way to get this to work with gtkpod please. :) Thanks!

---

### Post by martinrandau on 2009-09-14
I think I have the same problem with my ipod and also with a usb hd that worked well before. Perhaps a recent upgrade?

---

### Post by Literati on 2009-09-14
I'm not sure. My main PC, a Q6600 64-bit Jaunty machine recently died on me. So I'm stuck on an old Acer Aspire 5000 with an AMD Turion 64 running 32-bit Jaunty. 

A workaround I heard of was to run "modprobe -r ehci_hcd" but that doesn't work for me either, returning:

FATAL: Module ehci_hcd not found.

---

### Post by Literati on 2009-09-15
Shameless bump

---

### Post by Literati on 2009-09-16
:( Anybody?

---

### Post by Literati on 2009-09-17
Really hoping to be able to, you know, use my iPod...

---

### Post by Chronon on 2009-09-17
I don't even know if it's possible to mount those iPods as a storage device (MSC mode).  Have you checked to see if any MTP capable software can see it?

I run all of my audio players as UMS devices so I'm not familiar with MTP on Ubuntu.

---

### Post by PokerFacePenguin on 2009-09-25
I am not sure if this is your problem but this is what I did to fix connection problems with my nano 4GB blue IPOD....

I fired up a windows virtual machine and connected the usb port to my ipod.

Ejected it nicely.  Closed down the virtual pc.  Voila!  Magically my ipod icon showed up on my desktop and my apps could connect to it.  Ubuntu reported that the IPOD was corrupted and asked me if I would like to reinitialize it.  I said yes and then named the IPOD.  Now it works.

Was banging my head against the wall for a while thinking it was Ubuntu that was the problem when really in all likelihood I removed the IPOD during an operation and corrupted it.

Give it a try.  It can't hurt.

Good luck.

---

### Post by SPARTAN-118 on 2009-09-28
Hi, I don't get any messages, but my 4th Gen. Nano can't mount at all, my PC sees it as a "USB device" and when I double-click I can't mount!

I connected to Windows, went down to the "Safely Remove Hardware" icon and "Stopped" it. Then I rebooted, went back into Ubuntu, and it *still* can't connect!

I've had this problem earlier, no idea WTH is wrong.

Anybody help? :(

---

