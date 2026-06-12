---
title: "New Geek Squad UPS: How monitor?"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by halfB on 2007-08-06
Hey there!
I just picked up a cheap UPS with GeekSquad labeling.  For those not in the US, Geek Squad is a home brand for BestBuy stores.  It may be a rebranded CyberPower UPS.  How can I get my feisty system to monitor the UPS and is an automatic shutdown possible?
Thanks 
HalfB
	
Geek Squad® 875VA UPS/Battery Back-Up System
Model: GS-875U

---

### Post by kansei on 2007-08-06
Does it have a USB or serial port on it? If not, you probably can't monitor anything. Did it come with any windows software for monitoring.

---

### Post by pbcartwright on 2007-08-06
you might look at apcupsd
then look at /etc/apcupsd/apcupsd.conf . What you need to know is:


# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usb

---

### Post by halfB on 2007-08-07
It has both a serial and a usb connection option.  
And it came with windows software.
I will give a try with apcupsd.  
Thanks.
HalfB

---

### Post by cdrom600 on 2007-09-04
Did you ever get it working?

---

