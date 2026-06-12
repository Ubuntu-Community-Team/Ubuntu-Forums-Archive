---
title: "sonypi issues on a Sony Vaio VGN-BX196SP"
date: 2009-07-27
forum: Hardware
---

### Post by Another Monkey on 2009-07-27
Using Jaunty 9.04

This started out with me (unsuccessfully) trying to turn bluetooh off.  I know I can issue```
sudo /etc/init.d/bluetooth stop
``` but that doesn't actually switch bluetooth off on the Vaio.  Anyway, whilst looking for that solution I found out about "spicctrl" and so I installed it.

That didn't work because "sonypi" was not loaded, so I tried to load that.```
$ sudo modprobe sonypi
FATAL: Error inserting sonypi (/lib/modules/2.6.28-13-generic/kernel/drivers/char/sonypi.ko): No such device
```This *is* on a Vaio, so I have no clue what it thinks is missing and I am currently stuck with bluetooth always-on.

Anyone any idea how I can get "sonypi" to load so I can get control?

And would the lack of "sonypi" explain other problems I have having with AC/battery power detection, brightness etc.

I found [this]("https://help.ubuntu.com/community/SonyVaioBrightness"), but it was for 6.06!

This Vaio previously had a copy of XP on it which died a horrible and unrecoverable death (boot record) so it was wiped and Jaunty dumped on.  Bluetooth *may* have been turned off from XP (not sure), would that have any effect in Ubuntu?

Thanks!

---

### Post by Another Monkey on 2009-07-28
I tried this```
sudo mknod /dev/sonypi c 10 63
```and now when I try to load sonypi I still get```
insmod /lib/modules/2.6.28-13-generic/kernel/drivers/char/sonypi.ko 
FATAL: Error inserting sonypi (/lib/modules/2.6.28-13-generic/kernel/drivers/char/sonypi.ko): No such device

```but trying to run spicctrl now gives```
ioctl: Inappropriate ioctl for device
```
Is there a proper to remove the /dev/sonypi I created?  I just used "rm".  Anyway, I tried again with```
sudo mknod /dev/sonypi c 10 250
```and sonypi remianed unchanged, but spicctrl now reports```
/dev/sonypi: No such device
```So 63 would appear to be "more correct", but still wrong.

DOes anyone know how to get this working on a Vaio?

---

