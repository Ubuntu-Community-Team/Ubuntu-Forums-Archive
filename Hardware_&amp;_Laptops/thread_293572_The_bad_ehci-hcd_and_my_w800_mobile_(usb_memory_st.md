---
title: "The bad ehci-hcd and my w800 mobile (usb memory stick)"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by sideshowb0b on 2006-11-05
I'm trying edgy 6.10 after using fc5 for some time. I really like the feel of ubuntu and am thinking of changing over. Inevitably there are a few problems.

My sony ericsson w800 (similar to k750) plugged into fc4 and fc5 straight out of the box (using usb lead)

On edgy i get the following

# dmesg | tail 

usb 1-1: new full speed USB device using uhci_hcd and address 17
usb 1-1: device descriptor read/64, error -71

doing some extensive googling i found the following advice 

# modprobe -r ehci-hcd

this did the trick!

However what is ehci-hcd. I read somewhere that it is to do with fast usb transfers. Will my usb connection be slower if i stop ehci-hcd permanently?

More importantly - is this a bug  that might be causing other people grief?

I've tried it with another identical w800 and the same happens.

Cheers

Sideshowbob

---

### Post by sideshowb0b on 2006-11-07
and here i must blush with shame - it seems to have misteriously resolved itself?????

---

