---
title: "LCD monitor very dim with fresh 7.04 install"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by sc0ticus on 2007-07-17
This is my first linux install, as I've used Windows for the past ten years.

I've installed ubuntu 7.04 on a barebones system with onboard intel graphics. My lcd monitor appears very dark, to the point where it's almost unreadable.  When I've used it as an external monitor for my (windows) laptop, it is just fine.

I've checked for the obvious and the monitor brightness is already at max. (changing it doesn't do much) It is entirely possible that ubuntu has nothing to do with it, but I don't have a copy of windows to test it under another environment. So I'm doing my best to test things out.

This is a fresh install with no modifactions (no beryl, compiz, stuff like that). 

Could this be a intel graphics driver issue, a monitor driver issue? Are there settings in ubuntu that I'm not paying attention to like monitor brightness? The intel linux driver page says that the 950 should have support out of the box.

system:  [ASUS P3-PH4C Intel Socket T]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856110075")
graphics : Intel GMA 950
monitor: samsung syncmaster 170mp.

Thanks for any help you might have!

---

### Post by w4ett on 2007-07-18
If I'm not mistaken, Desktop monitor brightness is controlled within the monitor itself, and is not a function of the actual video driver installed.  Does the monitor have a menu/settings adjustment?....I'm not familiar with your particular model, but most have a capability to adjust brightness as well as horizontall and vertical position.

---

### Post by sc0ticus on 2007-07-18
Yes, I've already tried that. Unfortunately, it's not as simple as that.

What makes me suspicious is the fact that the monitor is brigth when used as an external for my laptop.  Searching around online has hinted at creating a file in /proc/acpi/video/VGA/LCD/brightness. Unfortunately, when I try to echo to it, I get the 'file not found' error. I've tried sudo'ing and it makes no difference.

I guess this question has evolved in to 'how do I write to /proc/acpi/video/VGA/LCD/brightness'? '/proc/acpi/video' exists, but there is nothing in it.

---

