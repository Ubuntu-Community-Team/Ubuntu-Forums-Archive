---
title: "How to Gracefully Shutdown w/ an On/off Switch, Not a Traditional Power Button"
date: 2014-07-19
forum: Hardware
---

### Post by kschiff on 2014-07-19
I have an Adlink ReadyBox 850 1U industrial type machine that initially came with windows (I swapped out the hard drive). This type of machine is typically used for signage type applications.

It has a rocker type on/off switch in the back, and when I go through the OS, the OS shutsdown, but the machine doesn't power off (I can still see the LAN link flashing). For now, once it reaches this state, I just turn the power off. I put a SSD in there, so boot up is very quick, but I'm thinking that it's not shutting down gracefully.

The machine has an an AMIBIOS 08.00.16

Am I worrying to much on this, or is there a way to ensure that this hard powers down from the desktop or via a script of some sort?

---

### Post by Yellow Pasque on 2014-07-19
Is Wake-on-LAN enabled in the BIOS and preventing clean shutdown?

---

### Post by kschiff on 2014-07-19
The BIOS doesn't have a wake on LAN option... although there was something to do with wake and USB and I disabled it.

For grins I tried to shutdown via terminal (sudo shutdown now)... the display became stuck on "restoring resolver state."

In the event that I just need to hard power down the machine each time, I modified grub to include: GRUB_RECORDFAIL_TIMEOUT=0

I also edited /etc/default/rcS to include FSCKFIX=yes to automatically check and fix file system on reboot... 

Not idea, but until I come up with a better answer.

---

