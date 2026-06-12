---
title: "Dell 2407WFP on GeForce Go 7300 with nVidia driver"
date: 2008-05-13
forum: Hardware
---

### Post by dmcn on 2008-05-13
Hardware: Lenovo 3000 N200 with GeForce Go 7300 256 MB - Dell 2407WFP
Software: Ubuntu 8.04 - nVidia driver 169.12 installed with EnvyNG

I'm trying to get my 24" Dell 2407WFP (1920x1200) to work as the primary display on my laptop, however I'm having no luck making nvidia-settings detect the resolution for the monitor. The monitor is detected but the only available resolutions are 320x240 and 640x480. On the same laptop, but with the 2408WFP, I have no problems at all. 

Is there any way of telling nvidia-settings what resolutions are available? I have the EDID-file from my 2408 which I guess should be usable by the 2407. 

Please note, I intend to use the display as the primary monitor with the laptop display turned off - when I'm away from the office I expect the laptop monitor to work as usual at 1680x1050. :)

---

### Post by dmcn on 2008-05-16
Am I the only one with this problem? :(

---

### Post by Mohonri on 2008-05-16
Nope.  I'm in the same boat.  I tried to upgrade my 7.10 machine to 8.04 and a bunch of stuff got borked.  So I did a clean 8.04 install, and once I enabled the nvidia proprietary drivers, it refused to recognize my monitor at all, and restricted me to 640x480 or 320x240.

GeForce 6200 on a Socket A platform, BTW.

---

### Post by Mohonri on 2008-05-19
I got mine working, thanks to this guide:

[http://ubuntuforums.org/showthread.php?t=596875](http://ubuntuforums.org/showthread.php?t=596875)

Apparently, there's something seriously broken in the drivers.  It may take a few tries to find a different driver that works, but I was able to get it working.

---

### Post by dmcn on 2008-05-20
Can you try running nvidia-settings and tell me what driver version is says you're running? Check the first view you get in the program. :)

---

### Post by Mohonri on 2008-06-04
I got it working with both the 100.14.19 and 169.07 drivers.

---

