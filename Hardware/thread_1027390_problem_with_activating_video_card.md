---
title: "problem with activating video card"
date: 2009-01-01
forum: Hardware
---

### Post by mvx on 2009-01-01
hey everyone im new to ubuntu so please explain things for a newbie if you can help me...

ive been trying to get ubuntu 8.10 desktop to activate my graphics card and nothing seems to work. im on a laptop, lenovo thinkpad t61, using Quadro NVS 140M. 

i cant get it to download/install using system>administration>hardware when i click activate on either 173, or 177, it just doesnt do anything. opens up a small notification box about downloading the drivers and just stays at 0%

i tried going through applications>add/remove and searched nvidia, tried to install 177, though it gave me in return an error;

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

ive also tried 173, same error...

if anybody could help me out, it'd b great!

---

### Post by iputz on 2009-01-01
I can confirm this error.

In the Gnome Desktop,
System > Administration > Hardware Drivers

The Hardware Drivers dialog tells me that I have no proprietary drivers in use on my system. It shows three NVIDIA accelerated graphics drivers: versions 173, 96, and 177, the last of which is recommended.

I can highlight the recommended driver and click the "Activate" button. This causes a "Reboot" symbol to appear next to the activated driver as well as the status message at the bottom: "This driver was just disabled, but is still in use."

I can then reboot back to the GDM greeter, which appears as a garbled, flashing, pixelated mess of console characters. As the GUI is very definitely unusable, I have to Ctrl-Alt-F1 to a console, run
```
sudo dpkg-reconfigure xserver-xorg
``` and reboot again. This gives my xorg.conf a nice enema, and I'm (probably) back to using vesa.

Dear nVidia,
Your driver sucks balls.
Sincerely,
iPutz

---

