---
title: "USB hard drive mount intermittent problem"
date: 2008-09-08
forum: Hardware
---

### Post by dormant on 2008-09-08
I am using a bus-powered USB hard drive to keep two Ubuntu computers synchronised.

The drive is formatted with a single ext3 partition and I use an rsync script to synchronise each computer with it. I always unmount the drive after use by right-clicking on the gnome desktop icon - sometimes I get a message telling me to wait, sometimes not. But I always wait for the icon to go away.

It works well and I use it every day. About once or twice a month I have problems mounting the drive. It appears in lsusb, but isn't mounted and doesn't appear on the desktop.

The only way I have found of sorting it is to run the Partition Editor and "check and repair" the parition.

My first guess is that the drive isn't being unmounted properly. Is there a better way of unmounting a USB drive?

Any other ideas welcome.

---

