---
title: "HP Elitebook 6930p install not possible?"
date: 2009-01-25
forum: Hardware
---

### Post by guzzi333 on 2009-01-25
Hi,

I've got a new HP Elitebook 6930p and I'm trying to run the live CD but the live it freezes somewhere in the boot sequence. I tried both 8.10 and the latest alpha of 9.04.

My Elitebook has the following hardware for wifi and display adapter

Intel Wifi Link 5300AGN
Mobile Intel (R) 4 Series Express Chipset Family

The booting goes fine when the progress bar still goes from left to right and back again, but when the real progress bar starts it stops at around 15%

Any ideas what's wrong?

I've read that people installed it successfully on a 6930p

What can I do more to find out what's wrong?

---

### Post by teaker1s on 2009-02-19
possibly the live cd does not have the correct driver for your hardware, if in doubt download the alternate iso and install from that as it has many more features

---

### Post by 00P2115 on 2009-04-02
1. To install, add with F6 

> acpi=off pnpbios=off

2. when booting for the first time, edit the command line with the same additions
3. sound at first only run through the headphones. Edit > /etc/modprobe.d/alsa-base

sudo vi /etc/modprobe.d/alsa-base

add the line:

> options snd-hda-intel model=laptop


Then everything should work.

---

### Post by ozorba on 2009-04-02
You may have to turn off "fan on ac always on" in the BIOS. That's how I got my one working.

---

