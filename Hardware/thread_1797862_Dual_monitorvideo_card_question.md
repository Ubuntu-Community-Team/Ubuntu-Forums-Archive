---
title: "Dual monitor/video card question"
date: 2011-07-05
forum: Hardware
---

### Post by Warthaug on 2011-07-05
I have worked in the past with ubuntu systems that have dual-monitors.  However, all of these were implemented by using two video cards.  I notice that many modern video cards claim to support multiple monitors on one card.  I may be mis-reading things, but it sounds like nearly every NVIDIA and ATI card currently in production has this capacity.

I am looking at setting up a new system with dual-monitors in the coming week or two, and was wondering:

1) Am I correct that these cards can support dual monitors on a single card?
2) Dues ubuntu work well with single cards supporting multiple monitors?
3) What cards would people recommend for use on a dual-monitor ubuntu system not requiring significant graphics processing?

Thanx in advance for any help

Bryan

---

### Post by CMOS4081 on 2011-07-05
Hi,
   I am currently using multiple systems with Nvidia Geforce graphics cards anywhere from Geforce 8600 GT, 9800GTX+/GTS 250, GTS450, GTX 465, GTX 580.
All with the current Nvidia drivers available from:  [http://www.nvidia.com](http://www.nvidia.com)

I have to warn you about some things.

1- I use Ubuntu 11.04 but use Gnome Classic I hate the new Unity so my advise is based on using Ubuntu Classic as the GUI.

2- Read around the forum on how to remove the opensource nouveau driver first before installing the nvidia driver.

The nvidia driver provides the nvidia-settings application (run as root or sudo) which is the Linux counterpart to the Windows Nvidia control panel, which allows you to setup the resolution and multiple monitors.

You can use different monitors and resolutions on each monitor.
Just as a recommendation try to run the native resolution on each display so things look better.

Good Luck! :P

---

### Post by wolfen69 on 2011-07-05
> **CMOS4081 said:**
> 
2- Read around the forum on how to remove the opensource nouveau driver first before installing the nvidia driver.


The nouveau driver is automatically disabled when you install the nvidia driver. No need to remove it. But I do recommend an nvidia card. Never had a problem with them.

---

### Post by Warthaug on 2011-07-19
Thanx everyone, things are working perfectly.

Bryan

---

