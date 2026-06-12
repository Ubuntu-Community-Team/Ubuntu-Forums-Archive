---
title: "External monitor (HDMI) as primary display ?"
date: 2023-12-17
forum: Hardware
---

### Post by oygle on 2023-12-17
The graphics card on a laptop has been giving errors and lately just see a blank screen, but it does work sometimes. I have been using an external monitor connected to the HDMI port, it is setup under display config. as a replica of the laptop screen. Can I change the system display configuration to only use the external monitor ? Set it as primary and disable the laptop screen ? Will that cause any problems with booting, and will it require some BIOS changes for the video/graphics ?

Basically change all configuration (BIOS and Display settings) so that the laptop screen is completely disabled, and Kubuntu only uses the external monitor through the HDMI port.

---

### Post by TheFu on 2023-12-17
That is controlled by the BIOS settings, almost always.  There are often some Fn+F4 type keystrokes to rotate between the different screen settings on laptops.  Extend, mirror, none,  Look on your keyboard for a Fn key and one of the F3/F4 keys to force the BIOS change to a running system.

---

### Post by mnymonyker on 2023-12-17
can't find delete button

---

### Post by oygle on 2023-12-17
> **TheFu said:**
> That is controlled by the BIOS settings, almost always.  There are often some Fn+F4 type keystrokes to rotate between the different screen settings on laptops.  Extend, mirror, none,  Look on your keyboard for a Fn key and one of the F3/F4 keys to force the BIOS change to a running system.

Thanks, found some info on the keyboard layout  ( [https://dl.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf?dgc=SM&cid=229826&lid=spr2277922014&linkId=66701883](https://dl.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf?dgc=SM&cid=229826&lid=spr2277922014&linkId=66701883) )  ..

> 
Some keys on your keyboard have two symbols on them. These keys can be
used to type alternate characters or to perform secondary functions. To type
the alternate character, press Shift and the desired key. To perform secondary
functions, press Fn and the desired key.
**NOTE**: You can define the primary behavior of the shortcut keys by changing
**Function Key Behavior** in BIOS setup program.

I notice F8 has icons of 2 screens, so that must be the one. Thanks  :)

---

