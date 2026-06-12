---
title: "Nvidia works great except when the xserver shutsdown"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by x001 on 2005-06-04
I have an alienware area51-m laptop. I got tired of windows and loaded ubuntu. To my suprise everything works without any modifications. I installed the nvidia driver from the universe packages. Everything worked perfectly even the built in wifi card works without any problem. I only problem that i incountered is when I attempt to shutdown/reboot the laptop i get a blank window and then wierd colors and line appear and move around the screen. This happens even when I switch to terminal window. Any help is appreciated.

Laptop Specs:
P4 3.4GHz
1024MB of RAM
NVIDIA GeForce FX Go5700 128MB of ram
60GB HD

I am still fairly new to linux so any assistance is highly appreciated.

---

### Post by codejunkie on 2005-06-04
this is not going to help fix it but  have always noticed that two on the top of the screen it scrambles like with red and green lines then shuts down it has done the same thing on three pc's with nvidia cards with every distro i've tried.

---

### Post by x001 on 2005-06-06
The weird lines and color appear when I close the lid and open it as well. The only way for me to get back to the desktop is to power cycle the laptop.

---

### Post by rjstevens3 on 2005-06-06
i noticed similar behavior in xorg until i corrected my xorg.conf. even though graphics displayed correctly most of the time, i had a few problems at startup and shutdown. i've noticed from other threads that nvidia cards have problems with what the monitor sends back through edid. try adding "IgnoreEDID" "true" under device section in xorg.conf. also make sure the resolutions and frequencies are right for your lcd.

---

### Post by xwang on 2005-06-18
[QUOTE=rjstevens3]i noticed similar behavior in xorg until i corrected my xorg.conf. even though graphics displayed correctly most of the time, i had a few problems at startup and shutdown. i've noticed from other threads that nvidia cards have problems with what the monitor sends back through edid. try adding "IgnoreEDID" "true" under device section in xorg.conf. also make sure the resolutions and frequencies are right for your lcd.[/QUOTE]

I have a similar problem with my Toshiba M30-304 (with  a Go5200 with 32MB). Often when I shotdown or reboot I have a "dirty" page and I have to turn off my notebook using the power button, but doing so I obtain currupted files when I restart my pc. Moreover sometimes I have a black screen during startup in the moment in which usually appear the nVidia logo and in this case i have the same problem with corrupted files.
If I had "IgnoreEDID" "true" in the device section of xorg.conf can I fix the problem.
Is it useful to reinstall the nvidia driver before?
If so how can uninstall the actual driver?
Thank you,
Xwang

---

### Post by aonegodman on 2007-12-14
I'm having similar items on my newly installed desktop after upgrading Nvidia driver through package. I had to reboot 4 or 5 times before monitor quit shutting off just it got to the Login Screen. It shut down my computer one time.

I had also set option 2 under(better graphics) desktop/screen resolution before last shut down.

Please explain how to apply the edits mentioned above to this newby on Ubuntu.

i.e  "IgnoreEDIT" "true" in device section of xorg.conf

Thanks!

---

