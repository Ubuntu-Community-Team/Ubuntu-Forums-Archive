---
title: "Selecting Hardware/Motherboard for a Linux Rig"
date: 2014-06-02
forum: Hardware
---

### Post by mysubs on 2014-06-02
How can I determine what hardware is likely to work best for Linux?  Is there an online resource somewhere I have yet to find?

Building exclusively Windows systems over the past 15 years has hamstrung me, now that I'm turning my attention to Linux.  I feel like I'm essentially starting over in terms of trying to figure out what hardware to work with.  Case and point, I recently started dual-booting 14.04 and W7; only to learn there aren't any readily available USB3.0 drivers for my Gigabyte motherboard ([GA-770T-USB3]("http://www.gigabyte.us/products/product-page.aspx?pid=3589&dl=1&RWD=0#ov")).

But this post isn't about my existing system.  I want to build a new rig, specifically for Ubuntu 14.04, no dual boot, just Linux.  I want to see what my options are and what I should look for when selecting my hardware, but I'm not sure where to start.  When I go to Newegg, Amazon, or my local Fry's retailer I have no idea how to determine what would be a good fit for Linux.

How can I figure this out?
Thanks!

---

### Post by TheFu on 2014-06-02
1) Stay with reputable, mainstream hardware vendors.
2) Check the HCL for Linux as a general guideline to start recognizing which things are well supported directly by the kernel. Vendor support is harder to handle than direct kernel support, which usually "just works"
3) There are many different sorts of "linux rigs" - server, file server, media server, media player, all have very different requirements.
4) I don't really deal with desktops much ... choosing a SuperMicro MB that is well supported by FreeBSD will usually mean it is also well supported by Linux. BSD is pickier.  The same goes for VMware ESXi "whitebox" HCLs ... they are pickier than Linux. "HCL" means "Hardware Compatibility List" - it is a common term. There are websites for this - "esxi hcl" is a good search term to find one.

Laptops tend to be hit or miss.  Best to always search for "ubuntu {insert laptop vendor and model} into google to see if anyone had issues with video, wifi or networking.  Newer models might have issues with the touchpad, though this seems to be relatively uncommon ... except for my new chromebook. ;)

When looking for add-on hardware, google the specific model+vendor and "ubuntu" for issues. Always search for "linux" in the reviews to see what works.  As an example, sometimes drivers become available under newer kernels - so negative reviews for 10.04 don't always mean it won't work on 12.04 or 14.04.  

Be careful with RAID cards, printers, and any funny add-on devices (TV tuners, etc.).  Find what someone else here is using and go with that is really the best idea.

Printers ... oh printers ... Look for 100% industry standard interfaces that don't need special drivers or GUIs for the printer to work. That has become popular on Windows recently, especially with cheaper printers.  I've been burned by Canon - in the end, it was less hassle to give away the printer and buy a well supported model (built-in support) from Brother or Samsung than to screw around with their half-assed attempts and odd drivers.  HP printers tend to be ok - but watch out for wifi models that need special drivers to work. Since I don't buy printers all that often, some of this might be dated. Do your own research.

Oh .... and avoid anything with "Windows" in the name. That is almost always a sure sign that it only work on Windows.   Remember the old "WinModems"? Those were death to Linux people.

Realtek network stuff tends to suck - try to stay with real Intel PRO/1000 NICs (though a few of those models have strange failures with VoIP traffic too). Google "ubuntu realtek network" to see more of my reasoning.

MB that need drivers loaded to work should be avoided. Almost all driver makers only support loading firmware from Windows now, which sorta defeats the purpose of having a Linux box.

In short - double, then triple check support. After being burned a few times, you'll get the hang of it. ;)

---

### Post by Yellow Pasque on 2014-06-02
Please be a bit more specific about what you want the new system to do and how much you're thinking of spending...

Phoronix is supposedly going to be reviewing more Z97 boards, but here is the first one:
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

> Realtek network stuff tends to suck
I disagree with that, at least for wireless, where I've seen issues with certain Intel chips as well.
I can't say I've had issues with my mobos with Realtek NIC's (8139, 8168 and possibly others).

---

### Post by mysubs on 2014-06-03
> **Temüjin said:**
> Please be a bit more specific about what you want the new system to do and how much you're thinking of spending...
This rig will need the least power.  Primarily used for word-processing and viewing multimedia, with some light-weight GIMP usage.  The most strenuous work it will do is viewing the occasional 1080p video, and periodic container encryption and decryption (using Truecrypt).

As for budget?  I'd like to get away relatively inexpensive, but also with modern hardware.

---

### Post by TheFu on 2014-06-03
I've run an AMD E-350 for this sort of use. That is an APU-type system, so not really recommended for general purpose needs.  The case, MB, PSU, RAM, were $150 at the time.  This was years ago and a 1-time deal from NewEgg.  I reused an old HDD, mouse, keyboard then connected it to a stereo and projector - poof - it is a media center machine.  Thanks to the AMD GPU (onboard), it easily handles 1080p videos with either h.264 or mpeg2 encodings. Any modern GPU system can do this too.  Other encodings are almost always 480p or lower resolutions - the CPU is powerful enough to handle them. I was trying to build a specific media center PC with low electricity use (just 26W), and ZERO sound from the PC.

Basically, any low end system can handle what you are asking today. I'd go with a low-end Core i3 to be safe and look for what other people have reported about Ubuntu/Linux compatibility. If you want to transcode videos, I'd bump up to a Core i5 CPU.  There are AMD equivalents for these things, I justs don't know what models are which with AMD.  The Core i3 and larger CPUs will use much more power than the APU models, but they also provide MUCH MORE processing capacity.

---

