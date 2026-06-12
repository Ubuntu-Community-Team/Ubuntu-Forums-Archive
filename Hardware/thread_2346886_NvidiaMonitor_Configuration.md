---
title: "Nvidia/Monitor Configuration"
date: 2016-12-19
forum: Hardware
---

### Post by Tikhon03 on 2016-12-19
I am helping a friend setup Linux on his computer. I do not have direct access to his computer right now, but I will have access tomorrow. It has an Nvidia GeForce 6150SE nForce 430. I tried installing the latest KDE version of Linux Mint. The nouveau drivers do not work well with it, so I selected the proprietary Nvidia 304.88 driver, but now it boots to a black screen. I can get to a command prompt. I have tried nouveau.blacklist=1 and nvidia.modeset=0  from the boot options with no improvement. I have tried nvidia-xconfig to generate an xorg.conf file, and when I looked at the file no information was included for the monitor (i.e. no resolution or refresh rate).  xrandr says "can't open display".  I actually have two monitors to work with, but both are old fashioned CRTs: a Dell E770s and an Optiquest Q71B8.  With the Optiquest I get an error: 
Invalid MIT-MAGIC-COOKIE-1 keyError: cannot open displayAt this point I'm not sure if the bigger problem is the Nvidia card or the monitor.  Perhaps simply getting a flat screen monitor would fix it, but if it is a configuration issue with Nvidia then the flat screen might still have the same issue.  If the above information is insufficient for diagnosis, I should be able to provide more tomorrow, but any suggestions about next steps would be helpful. Thank you.

---

### Post by xeronate on 2016-12-19
What type of connection are you using? The nvidia drivers fail for me when I use a VGA/DVI cord. Only HDMI and display ports seem to be working for me as of last week. I tried the latest releases of the last 5 drivers.

---

### Post by Tikhon03 on 2016-12-20
It is a VGA connection. I don't think the CRT monitors have an HDMI connection.

---

