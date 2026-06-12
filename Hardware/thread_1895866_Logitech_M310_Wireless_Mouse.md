---
title: "Logitech M310 Wireless Mouse"
date: 2011-12-15
forum: Hardware
---

### Post by fenash on 2011-12-15
Hello all! I have 10.10 Ubuntu and totally new to it so far but learning fast.
My problem is being forced to use the touchpad on my HP DV7 4272 due to my wireless mouse not working correctly.
Error i am getting is unable to enumerate device. So i have attempted to disable ohci_hcd.
That didnt work pending a reboot currently.
I reset and reconfigured hidpoint to no effect as well..
i cannot copy/paste with my touchpad (yet to figure out how) so i cannot give all the exact specifics. But i will come back to this thread hoping someone has a work around after i reboot shortly.
Thank you for your time and effort in advance!

---

### Post by wolfen69 on 2011-12-15
10.10 will no longer be supported in a few months. Can you get ahold of a more current version of ubuntu to try out the live cd? Support for hardware usually gets better as newer versions of ubuntu come out. 

If not, we'll have to think of something else.

---

### Post by fenash on 2011-12-15
wolfen69, thanks for the suggestion.... and 11.xx ubuntu runs like junk on my system, and no mouse there either. ive upgraded.. then when i saw how it ran, started over from scratch.
i love how linux runs on my system compared to windows 7 home premium. I bought an install disc from a shop and it installs most of the way and at the end says corrupt installation file... sigh... just wish i could use my wireless mouse, as i could get alot more done a lot more faster than with this junk touchpad on my laptop... 
i will likely get another win7 disc after x-mas and dual install linux next to it to experiment and tool around.
but as the upgrade to natty is now, its not worth it as it does not support my mouse either...
and to make matters worse i cannot get my NCsoft launcher to work in wine for City of Heroes... Still looking for a fix for that as well...

---

### Post by wolfen69 on 2011-12-15
Try
```
sudo apt-get install lomoco
```
[I]lomoco can configure vendor-specific options on Logitech USB mice (or
dual-personality mice plugged into the USB port). A number of recent
devices are supported. The program is mostly useful in setting the
resolution to 800 cpi or higher on mice that boot at 400 cpi (such as
the MX500, MX510, MX1000 etc.), and disabling SmartScroll or Cruise
Control for those who would rather use the two extra buttons as ordinary
mouse buttons. It can also retrieve battery level from wireless mice.[/I]

---

### Post by HandeH on 2011-12-24
Logitech M310 works out of the box in Lucid Lynx. Details of the mouse from lsusb are: ID 046d:c52f Logitech, Inc.
:D

---

