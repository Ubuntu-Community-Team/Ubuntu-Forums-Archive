---
title: "Touchpad going crazy"
date: 2015-07-20
forum: Hardware
---

### Post by nathanhurley on 2015-07-20
Hi. I have a Dell Studio One computer with touchpad on screen, and since upgrading from Windows to Lubuntu 15.04, the mouse randomly goes crazy for about 5 seconds about every 15 minutes. This did not happen on Windows. 

Please help. Thanks a lot!




nathan@nathan-Studio-One-1909:~$ uname -r
3.19.0-22-generic




nathan@nathan-Studio-One-1909:~$ dmesg | grep pnp
[    0.153380] pnp: PnP ACPI init
[    0.153955] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.155187] pnp: PnP ACPI: found 6 devices

---

### Post by Vladlenin5000 on 2015-07-21
Lubuntu would be my last choice for a touchscreen device (or anything else for that matter). 
Have you tested it before installing, in a live session?

---

### Post by nathanhurley on 2015-07-21
What would you recommend that is fairly lightweight and stable? I like Fedora, but would prefer to stick with something a little lighter.

---

### Post by Vladlenin5000 on 2015-07-21
The "lightness" comes mostly from the integration of a "light" desktop environment. 
Ubuntu and Lubuntu are the same under the hood. The difference is only between Unity (the former) and LXDE (the latter). Unity is a modern 3D DE which invariably needs more resources than LXDE, designed for lower end or older machines. Gnome, the one where Unity has its foundations and the most typical for Fedora isn't much less demanding, if any. Conversely, a Fedora running LXDE should be as "light" as Lubuntu...
But you don't need to go "light"... Your all-in-one PC isn't that old! ;-)
Besides, better touchscreen support should be expected from a "touch oriented" DE like Unity (or Gnome) then anything else. What can make a difference is the other drivers involved in the process, namely graphics drivers. Nvidia recommends 340.58 for your integrated Geforce 9400. You should find up to 346.xx in the Additional drivers utility. This are nvidia proprietary drivers that have been tested (by Canonical) and confirmed to work with a given Ubuntu release. 
Assuming you haven't installed it, you're then using the default open source driver. Try the proprietary drivers.

---

### Post by Shivakumar_Gurumurthy on 2015-07-30
It is still going crazy on my DELL Inspiron 13 7000 series.

I need to disable touchscreen to get mouse pointer back to normal.

---

### Post by ian-weisser on 2015-07-30
My touchpad 'went crazy' on an Acer laptop recently.
Not software related - an intermittent short inside the case. Resting my wrist in a certain spot flexed the plastic case just enough to cause the short.
Took about a week of trial and error to figure out the spot.

Your problem smells like hardware to me.

---

