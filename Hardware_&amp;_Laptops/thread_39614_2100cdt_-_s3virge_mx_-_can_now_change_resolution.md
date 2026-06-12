---
title: "2100cdt - s3virge mx - can now change resolution"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by direwolf on 2005-06-05
Brand: Toshiba 
Model: 2100cdt
CPU: K6-2 @ 400MHz
Mem: 64MB
Video: 2MB S3 Virge MX
Screen: 12.1" TFT LCD

Upon initial installs, I was stuck with a 640x480 resolution. I tried manually configuring my /etc/X11/xorg.conf file; a mistake for a novice like myself, this is my first "real" install of a linux distro for me, the others were only hd installs of live cd dirsto's. So anyway, I tried a few times and couldn't find anything that worked. Then, I must have done something wrong and the xserver couldn't be loaded.  So I started recovery mode and did a 

sudo dpkg-reconfigure xserver-xorg

For the most part I chose the defaults, the only things I chose myself were 
HorizSync "28-51"
VertRefresh "50-70"
DefaultDepth 24
Also, I did not allow the kernel framebuffer. 

I'm not sure if not allowing the kernel framebuffer is needed or not, I will ask about that later. In any case, I can now choose my resoution (800x600) rather than being stuck @ 640x480. 

I hope that this can help someone with the same problem now or in the future.

---

### Post by pzarate on 2006-02-02
Thank your article,  have the same problem with my "2100 cdt", in the night will test the xconf and next day comment my experience

---

### Post by direwolf on 2006-02-22
You might not want to use the xconf file directly ...I just got rid of it in the above post as I don't want anyone to use an old xconf (from 5.04) in a newer release (5.10 or 6.04, etc.) 

However, the main part still applies - 

sudo dpkg-reconfigure xserver-xorg

All of the defaults except: 
HorizSync "28-51"
VertRefresh "50-70"
DefaultDepth 24

I suspect that on clean Dapper installs - the process will have to be repeated.

---

### Post by Crumb on 2006-09-26
> **direwolf said:**
> Brand: Toshiba 
Upon initial installs, I was stuck with a 640x480 resolution. I tried manually configuring my /etc/X11/xorg.conf file; a mistake for a novice like myself, this is my first "real" install of a linux distro for me, the others were only hd installs of live cd dirsto's. So anyway, I tried a few times and couldn't find anything that worked. Then, I must have done something wrong and the xserver couldn't be loaded.  So I started recovery mode and did a 


I can't install XUbuntu on a K6-2/550+VirgeDX since the screen is limited to 640x480 and the install window is bigger so I can't click on "ok" or "cancel". I can't change the number of colours.

I can't change the resolution since the GUIs don't allow me to change the monitor type.

I wonder why I can't find any distro with a simple button with the label "monitor settings" that allows me to choose the maximum horizontal frequenzy and the the vertical one. Or the frequenzy of standard VESA modes, to make it easier for newbies like me.

the GUI is so simple that it doesn't allow you to do anything useful or if you want something more you have to learn "intuitive" commands :confused: 

I hope an ubuntu developer reads this so future releases include something to change the screen resolution and to create your custom modes.

Something like this [http://scenergy.dfmk.hu/amiga/images/pegasos/Pega2-ModeEdit.png]("http://scenergy.dfmk.hu/amiga/images/pegasos/Pega2-ModeEdit.png")

Commercial OSes developed by a handful of coders (like MorphOS) that work from time to time in their bedrooms include it... why Ubuntu can't have something like this? 

I guess some people will find my post funny but this makes me sad. I try out Linux from time to time and always find out that the GUIs aren't useful and I have to use the command line.

If the Ubuntu developers plan to make Linux more popular they should make the GUIs more useful.

---

