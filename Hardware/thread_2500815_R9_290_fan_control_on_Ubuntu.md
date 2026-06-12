---
title: "R9 290 fan control on Ubuntu"
date: 2024-09-12
forum: Hardware
---

### Post by mar.ste on 2024-09-12
Is my first graphic card (I have to use one to go from an integrated 2400G APU to a 5900X CPU).   


     The card is working but I'm not able to control the fan speed that  runs at  high speed (and noise).   

I tried with amdgpu-fan and corectrl but their  settings seems to have no effect on my card. 

Question is: how can I proceed further  in trying to manage the speed?   
           

IF useful, I'm on:
-  Ubuntu 24.04 LTS
-  MB Gigabyte [FONT=monospace][COLOR=#000000]B550M S2H[/COLOR]
- Card GIgabyte R9 290 Windforce
[/FONT]




Thank you!

---

### Post by QIII on 2024-09-12
Does your motherboard's firmware have GPU fan control?  It is almost always better to allow the mobo firmware to control fan speed rather than depending on slower software control.

---

### Post by mar.ste on 2024-09-15
Unfortunately not, it has just the control of the motherboard ones (CPU/case).

But I found that this graphic card has a switch with 2 positions, and on the second position it starts quieter (for some reason after a long time of switch off).

---

### Post by fonspatat on 2024-09-25
[COLOR=#131313][FONT=-apple-system]Switch positions: 

&#8220;**Quiet Mode**&#8221; &#8211; Bios position one. Switch is in position closest to where you plug in your displays. This mode is designed to optimally suit a gamer that wants to keep a tight lid on acoustics. If you do not play with headphones, you do not have a high end gaming chassis, or your room&#8217;s ambient noise level is extremely low this may be the mode for you.[/FONT][/COLOR]
[COLOR=#131313][FONT=-apple-system]&#8220;**Uber Mode**&#8221; &#8211; Bios position two. Switch is in position furthest away to where you plug in your displays.[/FONT][/COLOR]
[COLOR=#131313][FONT=-apple-system]The Uber mode is designed to perform optimally under all performance and game testing. This includes crossfire. [/FONT][/COLOR]
[COLOR=#131313][FONT=-apple-system]If you are in Uber mode you get a higher TDP limit which helps in manual overclock, you should also get more Voltage limit for your OC and you will have fixed clocks (without Boost). As such in normal QUIET mode the GPU is switching clocks between 800 base and 947 MHz max clocks based on TDP / Power limiter / Temp envelopes. Overall you'll see the GPU's clock anywhere at  900-947 MHz, but mostly it's boosting the full 947 MHz.

[https://www.reddit.com/r/Amd/comments/hizdal/what_is_this_tiny_3way_switch_on_my_gpu_radeon_r9/](https://www.reddit.com/r/Amd/comments/hizdal/what_is_this_tiny_3way_switch_on_my_gpu_radeon_r9/)[/FONT][/COLOR]

---

### Post by mar.ste on 2024-10-08
I've found in this thread [https://unix.stackexchange.com/questions/627182/how-to-lock-fan-speed-for-amd-gpu-in-ubuntu-20-04](https://unix.stackexchange.com/questions/627182/how-to-lock-fan-speed-for-amd-gpu-in-ubuntu-20-04) that is possible to monitor and to control graphic cards via device filesystem.  I checked and on mine I've found my card in the /sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0 directory.  Question is: where to find some documentation of these files and how to use them? (i.e. in my case to control the fan speed)

---

