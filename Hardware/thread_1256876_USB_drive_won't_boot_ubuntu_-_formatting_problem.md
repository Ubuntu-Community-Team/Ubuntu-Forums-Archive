---
title: "USB drive won't boot ubuntu - formatting problem?"
date: 2009-09-03
forum: Hardware
---

### Post by Scubdup on 2009-09-03
I've tried using the included liveUSB creator and Unetbootn (tried Ubuntu and damn small linux) and neither have produced a bootable disk (despite both registering success).

The resultant USB drive fails to boot any of my three machines.

Despite trying to use fdisk to delete all existing partitions and then create a new one, I still get an message when I type:

sudo fdisk /dev/sdc

which says:-

*"The number of cylinders for this disk is set to 1062. There is nothing wrong > with that, but this is larger than 1024"*

This is despite trying different numbers of cylinders when using fdisk to create the partition.

The pen drive seems to work fine otherwise.

Could it be a problem that the USB drive is 2Gb?

Any assistance would be gratefully appreciated.

---

### Post by dandnsmith on 2009-09-03
> **Scubdup said:**
> 
Could it be a problem that the USB drive is 2Gb?

Not as such - I've created several distros on 2G sticks, and have one on 4G working quite happily.

Can you try it on someone elses machine(s)? - could be that you just happen to have several for which it won't work.

There are sections on pendrivelinux.com which deal with testing a particular PC for ability to boot from such a drive.

---

### Post by Scubdup on 2009-09-03
> **dandnsmith said:**
> Could be that you just happen to have several for which it won't work.Jees, I hope not! That would be pretty unfortunate.> **dandnsmith said:**
> There are sections on pendrivelinux.com which deal with testing a particular PC for ability to boot from such a drive.Thanks for that. That looks very helpful. I'm gonna give it a try.

Direct link in case others are after it:

[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

---

### Post by sblunix on 2009-09-03
> **Scubdup said:**
> I've tried using the included liveUSB creator and Unetbootn (tried Ubuntu and damn small linux) and neither have produced a bootable disk (despite both registering success).

The resultant USB drive fails to boot any of my three machines.

Despite trying to use fdisk to delete all existing partitions and then create a new one, I still get an message when I type:

sudo fdisk /dev/sdc

which says:-

*"The number of cylinders for this disk is set to 1062. There is nothing wrong > with that, but this is larger than 1024"*

This is despite trying different numbers of cylinders when using fdisk to create the partition.

The pen drive seems to work fine otherwise.

Could it be a problem that the USB drive is 2Gb?

Any assistance would be gratefully appreciated.
Be sure to make sure that the partition on the Flash Drive is flagged as boot (you can do this using gparted) and also be sure that your computer's Boot settings boot USB Drives before Hard Drives...

---

