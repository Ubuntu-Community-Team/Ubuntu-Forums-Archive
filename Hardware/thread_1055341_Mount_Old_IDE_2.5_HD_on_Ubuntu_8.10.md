---
title: "Mount Old IDE 2.5 HD on Ubuntu 8.10"
date: 2009-01-30
forum: Hardware
---

### Post by MSwal2846 on 2009-01-30
I have an old IDE 2.5 Harddisk that I thought I would try to use to back things up.  I have a USB IDE/SATA connection adaptor that connects to the old drive.  When I plug it in to the USB port, nothing seems to happen, other than the activation light lighting up on the adaptor.

sudo fdisk -l didn't find it.

So I thought I'd mount it:

mswallow@mswallow-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
mount: special device /dev/sdb1 does not exist


When I run dmesg as I plug it in, I get:
[ 2770.454568] usb 4-1: new high speed USB device using ehci_hcd and address 6
[ 2770.586544] usb 4-1: configuration #1 chosen from 1 choice
[ 2770.587295] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2770.587521] usb-storage: device found at 6
[ 2770.587523] usb-storage: waiting for device to settle before scanning

and then I get rows and rows of:
[ 2036.534843] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 2036.534848] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information

I do have ntfs-3g and ntfsprogs installed.

Can someone tell me in English what these messages mean and how I can correct this?

Thanks!!
Mark

---

### Post by bettlebrox on 2009-01-30
I'd say it's one of 3 things! :)

[LIST]
[*]The drive is failing
[*]The drive isn't connected to the enclosure properly (or the connectors in the enclosure are flakey).
[*]It's related to this bug:
[INDENT][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)[/INDENT]
[/LIST]

If it's related to the bug report you'll have to upgrade to 2.6.28. I'm not sure the easiest way to do that, but ask and I can try and find out.

---

### Post by MSwal2846 on 2009-01-31
Thanks, brettlebrox.

It occured to me that this disk may be password protected ... I hadn't thought about that before today.  I wonder if that's part of the issue.  I've had the hd for quite awhile ...

Let me play around a little more and see what I can find out.

Thanks for the other leads...

Mark

---

