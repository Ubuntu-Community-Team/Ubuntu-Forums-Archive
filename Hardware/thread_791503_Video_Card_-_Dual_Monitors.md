---
title: "Video Card - Dual Monitors"
date: 2008-05-12
forum: Hardware
---

### Post by dave9191 on 2008-05-12
Hey guys, 

I have finally rejoined the Ubuntu community after missing out a number of distros. I am using Ubuntu at work (took a bit of convincing ;) ). 

I need to hook up a second monitor to my machine and for that I will need to buy a new graphics card. The question is .. which card?

I need a card for:

- For work related stuff, programming, web. 
- Dual monitor support (both VGA). 
- Works with ubuntu and give some desktop effects. 
- PCI-E card. 
- Extending the desktop, not just cloning it. 
- The cheapest good card I can get ( preferably about £20 )

I was just going to get an MSI one, but then I found a post saying it doesn't work with a vga monitor connected to the DVI port. And another post mentioning that you can can only clone the display on the cheaper model of the MSI card. 

So any advice would be great. Preferably tried and tested solution :)

Thanks in advanced.

---

### Post by Adrian1978 on 2008-05-12
i don't know about the prices, but a year ago i bought a Geforce 7300 GS and i use it in dual monitor, side to side, with 2 syncmaster monitors, i managed them with the nvidia x server settings and everything worked fine. Now i'm using a dell notebook and other monitor and i also manage them wth nvidia x server with no problems.

---

### Post by gas, meet foot on 2008-05-12
From my research, the easiest way to get it working is a single nVidia card with dual heads and two monitors that are as similar as possible.  They should support the same resolution, color depth, and refresh rate.  Don't try to mix an LCD with a CRT.

---

### Post by compgeek83 on 2008-05-12
just setup dual-monitors this morning under 8.04, in fact this will be my first full day running Linux as my primary OS (I've been using it under VMware Player for a few weeks).

I'm running an eVga PCI-Ex 8400GS with 512mb onboard, I have 2 dell flatscreens, a 1901FP and an E196FP, (ones 5 years old and ones 2 or so probably), both 19in with almost exact specifications.

setup was a little funky at first but with a little play it worked, once I learned I had to install nvidia-settings seperately and that it wasn't installed by enabling the nvidia drivers.  I had to set-up the monitors the way I wanted them in nvidia-settings and then click "save to x configuration file" only it wouldn't save by itself so I have to manually edit my xorg.conf file and copy and past from nvidia-settings preview window to xorg.conf.  I rebooted and now I'm up and running fine.

---

### Post by dave9191 on 2008-05-13
Thanks for the replies guys, 

I've found a EVGA GeForce 8400GS 256MB DDR2 PCIE HDTV DVI 450/800MHz for around £22. 

compgeek83, do you use the dvi connector to connect up one of your screens? I am worried that some cards do not support dvi to vga converters to hook up 2 vga monitors. 

I might give that a shot soon, unless someone knows something bad about that card.

---

