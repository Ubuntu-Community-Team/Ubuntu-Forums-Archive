---
title: "Screen Brightness"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by skartel on 2007-10-05
Hello, 

I was wondering if there was a utility built in, or even some kind of third party application that would allow me to adjust my screen brightness in ubuntu. 

The reason I ask is I have just installed ubuntu and set everything up, but my screen has an issue where it blacks out every so often, and in windows the way i resolved this was to turn down the brightness from the high setting. 

Is there anyway I can do this in ubuntu? I really want to switch :)

Thanks

---

### Post by BoomerET on 2007-10-05
Skartel,

First off, is acpi turned on (aka Power Management)

I don't know if this would work for you, but it's what I use on my Panasonic Toughbook CF-19.

echo 21 > /proc/acpi/pcc/ac_brightness

You probably have to do this as superuser, or maybe sudo. 

Or, use dc_brightness

Again, on my Panny, the valid values are 1-21.

I had to write a custom app that I put on the taskbar to bring up a slider widget to adjust the brightness.  

There may be such an animal built-in, but we're using an old version.

Boomer

---

