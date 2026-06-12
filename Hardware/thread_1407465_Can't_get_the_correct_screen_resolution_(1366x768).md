---
title: "Can't get the correct screen resolution (1366x768)"
date: 2010-02-15
forum: Hardware
---

### Post by raccoss on 2010-02-15
Hi guys.

This is my first post on this forum. I apologize in advance if I posted in the wrong section and for my english.

I bought 3 days ago an ASUS laptop. Series X52.
Graphic card ATI Radeon Mobile HD 5470.

The fact is that Gnome (in my case is Linux Mint 8, based on Ubuntu 9.10) cant recognize the monitor and so it set the display to "default". It means that I have a 1024 x 768 (stretched) resolution instead of 1366 x 768. 
If I try to configure X-Org with the correct resolution, it says that this resolution is not supported by the display.

It's a fact that ATI or others hasn't (yet?) released drivers for linux for the HD 5000 series.

For the moment, I just need to get a resolution ratio of 16:9, in order not to see every image stretched. So, what's your advice?

a) It's a matter of the display. I should try to discover the manufacturer of the display and then reconfigure X-Org.
b) It's a matter of the graphic card. I should try with other graphic card drivers, maybe ATI Radeon series 4000
c) Don't waste time. Hope and wait for correct drivers.
d) Nope. Bring the laptop back to the shop.
e) Random insults.

Thanks.

---

### Post by hxcobd on 2010-02-15
B first and foremost, followed by possibly A.

For a newer video card, there WILL be a solution, so definitely don't just give up. Try a few different related drivers from the ATI site. Make sure you've tried the Hardware Drivers (Jockey) driver-add, as well as FGLRX from the repo.

---

### Post by sleepitoff on 2010-02-17
There's some info here: 

[http://ubuntuforums.org/showthread.php?p=8817255](http://ubuntuforums.org/showthread.php?p=8817255) 

Good luck, I'm stuck in 800 x 600 with this one.

---

### Post by JerichoKru on 2010-02-17
> **raccoss said:**
> Hi guys.

This is my first post on this forum. I apologize in advance if I posted in the wrong section and for my english.

I bought 3 days ago an ASUS laptop. Series X52.
Graphic card ATI Radeon Mobile HD 5470.

The fact is that Gnome (in my case is Linux Mint 8, based on Ubuntu 9.10) cant recognize the monitor and so it set the display to "default". It means that I have a 1024 x 768 (stretched) resolution instead of 1366 x 768. 
If I try to configure X-Org with the correct resolution, it says that this resolution is not supported by the display.

It's a fact that ATI or others hasn't (yet?) released drivers for linux for the HD 5000 series.

For the moment, I just need to get a resolution ratio of 16:9, in order not to see every image stretched. So, what's your advice?

a) It's a matter of the display. I should try to discover the manufacturer of the display and then reconfigure X-Org.
b) It's a matter of the graphic card. I should try with other graphic card drivers, maybe ATI Radeon series 4000
c) Don't waste time. Hope and wait for correct drivers.
d) Nope. Bring the laptop back to the shop.
e) Random insults.

Thanks.

Have you tried these?  [http://support.amd.com/us/kbarticles/Pages/ATI-Catalyst-driver-Radeon-HD5400.aspx](http://support.amd.com/us/kbarticles/Pages/ATI-Catalyst-driver-Radeon-HD5400.aspx)

---

### Post by TangoRom on 2010-03-28
try this, all the way to the bottom:

[http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=128752](http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=128752)

let me know.

---

### Post by efflandt on 2010-03-28
You may find that X does not have a 1366 mode.  When using cvt or gtf to find a mode, the next step above 1360 was 1368.  When I looked through /var/log/Xorg.0.log, it did list a 1360x765 mode and a 1360x768 mode, but it said the latter had too many lines.  Since WinXP seemed to use 1360x764, I used cvt to find a 1360x765 modeline and that worked great.

Although, I know nothing about xorg.conf and it was for different video card with standard modules on an external display "sometimes" used with a laptop.  So I used xrandr commands in a script to set the 1360x765 mode.

A laptop with old ATI video and standard modules would only do 1360 maximum, so I used a 1360x768 mode when I connected that to a 1080p display.

---

### Post by 2hot6ft2 on 2010-03-28
> **efflandt said:**
> You may find that X does not have a 1366 mode.  When using cvt or gtf to find a mode, the next step above 1360 was 1368.  When I looked through /var/log/Xorg.0.log, it did list a 1360x765 mode and a 1360x768 mode, but it said the latter had too many lines.  Since WinXP seemed to use 1360x764, I used cvt to find a 1360x765 modeline and that worked great.

This wont help the OP at all.
I don't know about "cvt or gtf" but 1366x728 is definitely a supported resolution. Since that's what my NVIDIA is on a 15.4" HP laptop.

---

