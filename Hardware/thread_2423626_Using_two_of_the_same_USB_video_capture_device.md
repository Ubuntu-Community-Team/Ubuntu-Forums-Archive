---
title: "Using two of the same USB video capture device"
date: 2019-07-26
forum: Hardware
---

### Post by andytij81 on 2019-07-26
Hi All

I have two EasyCap USB video capture devices which I have two CCTV camera plugged in to.

I would like to be able to capture still from each of these using motion.

There is a bit of a bodge to get them working, which I do using a shell script on startup.

```
#! /bin/bash


sudo modprobe em28xx card=64
echo eb1a 5124 | sudo tee /sys/bus/usb/drivers/em28xx/new_id

```
However, it only picks up one of the USB capture devices, not both.

Running the command twice does not pick up the second device.

Both USB video devices appear in in lsusb, and the both the devices audio inputs - which use the AC97 driver - appear in arecord -l

I just don't get beth devices appearing in /dev

Any ideas?

Thanks
Andy

---

