---
title: "constant beeps on startup etc."
date: 2009-08-18
forum: Hardware
---

### Post by fela on 2009-08-18
Immediately after I hit the Ubuntu entry in my grub menu, the system starts frantically beeping over and over again multiple times per second. The system seems to boot fine (although the HDD is getting quite old) - and the beeping stops when I get to the GDM, the same time as my graphics driver kicks in and controls the fan on my graphics card. After I log in, if I switch to a console it does the same beeping until it's reached the console (usually takes a couple of seconds to reach it from GDM). The only thing that's changed is that I've installed a second monitor. It was trying to display a 1440x900 framebuffer resolution on the new (square, 1280x1024) monitor - it of course gave me a warning on startup, and now I've changed the /etc/usplash.conf and also I've changed the grub menu to read vga=791 (that's always failsafe on anything bigger than 1024x768 isn't it?). I'm gonna try to reboot now and see if it still happens.

My motherboard is a gigabyte GA-M52L-S3, I didn't see anything in the manual about constant beeping. If it was a hardware failure it would have to be my Linux harddrive as that's the only thing that differs from the hardware that windows uses (and it seems to be working fine right now) - windows works and from my experience that seems to crash at the slightest hitch! :lolflag:

---

### Post by fela on 2009-08-18
UPDATE! Please do not reply to this thread as it's resolved. Turned out it was something to do with trying to display 1440x900 resolution on a LCD that couldn't handle it. Now I'm using 1024x768, I'll change it to 1280x1024 when I get the chance :) And no more beeping for me!

---

