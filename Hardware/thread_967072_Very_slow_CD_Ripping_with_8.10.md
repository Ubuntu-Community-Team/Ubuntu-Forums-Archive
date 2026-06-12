---
title: "Very slow CD Ripping with 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by econtrerasd on 2008-11-01
I know this has been an issue before on other versions of Ubuntu, but none of the fixes that I've checked on the forums seems to help.

I have a Dell Inspiron 1520 equipped with a combo cd-rom, dvd-writer it works ok by all means but when ripping it gives a performance of 1.5x of speed which results in 40 minutes time for ripping a regular music cd.

This is of course VERY slow and annoying of course

I tried getting some info on the drive with the following command:
[I]
neto@LaptopDell:/$ hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

[/I]I do get a mess*a*ge stating an invalid Ioctl for the device but I have no idea if this is the error I'm looking for or what to do to fix it.

Any insight will be very much appreciated

Regards!

---

