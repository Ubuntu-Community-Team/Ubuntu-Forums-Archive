---
title: "Can't detect nor mount usb devices"
date: 2010-07-21
forum: Hardware
---

### Post by SeePU on 2010-07-21
I thought I'd post this since I'm curious if anyone recognizes or can explain this condition.

The machine is a Thinkpad T41 with two USB ports.  There is a problem with them, though.   I think a lot has to do with the 2.0 functionality.  I ordered a PCMCIA card hoping that will solve it.  However...

Here's some facts/info:
*Debian Squeeze LXDE - usb devices will *mount* with some CLI tweaking - various commands will eventually get it to work - it doesn't mount automatically though
*Ubuntu/Lubuntu 10.04 - none work - Usb flash drives or usb-connected HDDs - removing the ehci_hcd module results in the infamous FATAL:  ***...module not found message.  Trying the same sequence (as the Debian install) doesn't work
*usb mouse works

I was just wondering if there is some explanation for this and only asking because I can get things to work in Debian.  Is there something different that Ubuntu is doing or?  I hope the PCMCIA card will solve all this and that the drives will be detected and mounted automatically, though.  But, I have to wait at least two weeks for it to arrive. 

When I try commands such as dmesg... the usb devices will 'not enumerate.'  This also displays on boot up.  

Anyone know if there is bug in Ubuntu 10.04 that it cannot deal with 'usb 2.0' "issues."  I suspect the Debian install detects a problem with the usb ports and is only using 1.1 speeds although it's utlizing the usb 2.0 functionality (which probably doesn't work anymore).  But, Ubuntu 10.04 is not doing this?  It simply won't adjust anything and doesn't detect any usb 2.0 port or usb 2.0 device there????

Help?!? :( ;)

---

### Post by cliffdodger on 2010-07-21
Well I don't have a solution for you but I can tell you that the only time I've had a problem with USB devices not mounting (so far) in Ubuntu is particularly when I am running it in Sun Virtual Box on Windows XP (don't panic! I have my reasons!)

In that case - anytime I plugged in a usb device and tried to assign it to the virtual ubuntu install virtual box and ubuntu would freeze completely.

But no - the OS itself normally handles USB 2.0 just fine. Could be an oddity specific to your laptops USB controller but I would think those are pretty universal devices, even on laptops.

---

### Post by SeePU on 2010-07-21
> **cliffdodger said:**
> Well I don't have a solution for you but I can tell you that the only time I've had a problem with USB devices not mounting (so far) in Ubuntu is particularly when I am running it in Sun Virtual Box on Windows XP (don't panic! I have my reasons!)

In that case - anytime I plugged in a usb device and tried to assign it to the virtual ubuntu install virtual box and ubuntu would freeze completely.

But no - the OS itself normally handles USB 2.0 just fine. Could be an oddity specific to your laptops USB controller but I would think those are pretty universal devices, even on laptops.I think so but was wondering why I can eventually get my usb drives to get detected in Debian Squeeze LXDE but none of the *ubuntus.  I tried ver. 10.04.  I tried the same steps to get the drives initialized but it only worked in Debian.  

Debian Squeeze is at a similar state as 10.04, is it not?  Anyway, it's more of an annoying circumstance if the PCMCIA USB card makes the issue redundant but it would be nice if I was not forced to load Debian each time I want to use one of my usb thumb drives or my 1TB SATA HDDs (using usb connection with the laptop since it doesn't have eSATA)! :-/

---

### Post by SeePU on 2010-07-23
> **cliffdodger said:**
> Well I don't have a solution for you but I can tell you that the only time I've had a problem with USB devices not mounting (so far) in Ubuntu is particularly when I am running it in Sun Virtual Box on Windows XP (don't panic! I have my reasons!)

In that case - anytime I plugged in a usb device and tried to assign it to the virtual ubuntu install virtual box and ubuntu would freeze completely.

But no - the OS itself normally handles USB 2.0 just fine. Could be an oddity specific to your laptops USB controller but I would think those are pretty universal devices, even on laptops.It might be.   But, I ordered a usb cardbus for plugging in the cardbus slot.  I'm hoping the dual usb ports provided will allow for auto detect or at least elimination of any hardware problems.

However, I'm posting this because, amazingly enough, my usb hardware was detected automatically just now.  I don't have any explanation.  It's very strange and I can't explain it.

Is there a way I can trace what happened?  Some log I can read?  Any commands that I can run?

Maybe dmesg?

---

