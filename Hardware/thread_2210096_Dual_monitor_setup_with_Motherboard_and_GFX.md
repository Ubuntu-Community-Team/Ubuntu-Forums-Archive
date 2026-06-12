---
title: "Dual monitor setup with Motherboard and GFX"
date: 2014-03-09
forum: Hardware
---

### Post by myles4 on 2014-03-09
Motherboard: AsRock Z77 pro 3
Gfx: GTX 660 TI

My computer recently had a huge problem and I wasn't able to reinstall windows through any means, nor boot my backup windows copy. I had 2 monitors set up, but due to the lack of compatible cable plus aging monitors I needed two open VGA ports which happened to be one on my Gfx and one on my Mobo. It worked fine in windows, but with Ubuntu(Was running mint before and nothing there either) it's on but not receiving picture, nor is it detected by the system settings. Note: On Kali linux it dumped a bunch of running code on the second monitor.
I'm not new to Linux, but this is my first time using it as a primary OS, so assume I know the basics. [If anyone knows how to run Saints Row 3&4 I'd appreciate the knowledge]

Also, unrelated question: 
I have the Grub from Mint still installed, but it doesn't show Ubuntu. When I boot I type "c" (for command line) and then just type "exit" and it brings me to the Ubuntu grub so I'm not sure if I'm supposed to remove it or what to do.

All help is appreciated!

Regards, 
Myles

---

### Post by Mark Phelps on 2014-03-09
It's always best to deal with ONE problem at a time, not a list of them.

As to the video, we need more information:
1) what is the make and model video chipset on the mobo?  IF you don't know, open a terminal, enter "lspci", look for the line containing "VGA" and post the results back here.
2) What version of Ubuntu are you running?
3) When running Ubuntu, which of the two monitors is showing the screen -- the one connected to the video jack on the Mobo, or the one connected to the video jack on the GTX card?

---

### Post by myles4 on 2014-03-09
Ah right,
1. 01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 660 Ti] (rev a1)
That's for my GFX though, no other VGA line. Upon further inspection, it seems that it was using my CPU's integrated Intel HD 4000 Graphics[Intel 3570k].
2. 12.04 LTS (Not sure if I should upgrade)
3. The one connected to the Graphics, that one has always been primary on every OS. Also windows used a generic driver for me second monitor for display, it's some cheap Compaq widescreen I found at a yardsale. Primary is connected to a DVI port with a VGA converter. Other is connected directly.

---

### Post by myles4 on 2014-03-23
Bump

I still haven't figured this out. I upgraded to 13.10.

---

### Post by Mark Phelps on 2014-03-23
Sorry I didn't get back -- but not an expert with Nvidia graphics.  From my experience, Linux doesn't work with two different video drivers.

Perhaps someone more versed in Nvidia cards can help.

---

