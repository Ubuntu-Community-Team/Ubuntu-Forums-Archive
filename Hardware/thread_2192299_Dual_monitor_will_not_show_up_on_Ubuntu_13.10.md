---
title: "Dual monitor will not show up on Ubuntu 13.10"
date: 2013-12-07
forum: Hardware
---

### Post by fried1ninja on 2013-12-07
Hello everyone, this is my very first forum post. I am very new to Linux in general. Although I have been using it for over a year now (and I love it), I still don't know any advanced stuff. 

So I'm posting because I ran into an issue. My second monitor I plugged into my VGA port, does not show up anymore. It was working not even 15 minutes ago, but I unplugged it to take a single monitor screenshot. When I turned it back on, there was nothing. I went into settings - displays. It showed my second monitor, but it was disabled. I enabled it, and adjusted the settings. My native resolution on my second monitor is 1920x1080, but Ubuntu was only showing the 1600x900. I went with that just to see if it would at least display on my second monitor. But it spit an error at me: 

*"The selected configuration for displays could not be applied*
*required virtual size does not fit available size: requested=(1600, 1668), minimum=(320, 200), maximum=(1600, 1600)**"*

Note that it was working perfectly with 1920x1080 before I unplugged the VGA cord. Also I do have proprietary graphics drivers installed. 

Specs: 
Model: HP Notebook 2000-329WM
Processor: AMD E-350 1.6 GHz [Dual Core]
Laptop Display: 15.6 inch LED Backlit, integrated (laptop)
Second Display: Sceptre E328BV-FMDC 32-inch 60Hz LED HDTV (Yes I know it's a TV, but it works great)
OS: Ubuntu 13.10 stock with other DE's installed (Mostly use Unity for convience.)

Any questions, ask away. I will reply to them ASAP.

---

### Post by fried1ninja on 2013-12-07
I figured it out. 

I logged out of Unity into GNOME 3, and the display started to show up in GNOME 3. I adjusted the settings, and logged back into Unity. It's working great again. 
Sorry for your troubles everybody, this forum is *solved*.

---

