---
title: "Flash Drive Kills USB System"
date: 2009-04-08
forum: Hardware
---

### Post by theshibboleth on 2009-04-08
Hi, I'm having a problem where after I plug in my flash drive no usb devices plugged in (including the flash drive itself) work. If no other devices are plugged in I am at least able to write data to the flash drive,

This has occurred with two separate devices, an iPod and a nondescript thumb drive.

I am usually able to get usb to work again by running sudo rmmod ehci_hcd
and then sudo modprobe ehci_hcd, but sometimes I actually have to restart.

This issue does not occur when I'm in Windows, which suggests to me that it's a software bug or at least software the software could be made to work around.

I'm running the 64-bit version of Ubuntu 8.04.2.

I'm probably going to file a bug report, but I wanted to make sure that this wasn't a known issue or that there was some sort of solution to this problem, and I'd also like some advice as to what log files I should look at to find at what's going on. Thanks.

---

