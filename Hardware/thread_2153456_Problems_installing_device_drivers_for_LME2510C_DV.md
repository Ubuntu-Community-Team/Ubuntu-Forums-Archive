---
title: "Problems installing device drivers for LME2510C DVB-S device"
date: 2013-06-11
forum: Hardware
---

### Post by erbachem on 2013-06-11
Hi All,

I'm in the process of installing the device drivers from LinuxTV for a no name brand LME2510C USB based DVB-S tuner (ID 3344:22f0). I've been running through the install instructions provided by LinuxTV and have gotten as far as the testing stage. Here's a portion of what I can see when I run lsmod...

dvb_usb_lmedm04        19067  0
dvb_usb_v2             23380  1 dvb_usb_lmedm04
dvb_core               90348  2 dvb_usb_lmedm04,dvb_usb_v2
rc_core                21206  2 dvb_usb_lmedm04,dvb_usb_v2


The next step is to check for /dev/dvb. Unfortunately, this directory doesn't exist. 


I'm looking for advice on next steps for troubleshooting. I'm new to linux so short, simple sentences are preferred :). 

Any assistance would be much appreciated.

---

### Post by erbachem on 2013-06-14
Hi All,

Still looking for some help on this. The LinuxTV site advises that the /dev/dvb directory should have been added automatically by udev. It also talks about using modprobe to manually add using the appropriate modprobe command. Not sure what's appropriate.

What should I be looking for? Is this in the right area? Should I try re-asking the question on the noob forum?

---

