---
title: "HDMI issues on Ati HD 4670"
date: 2011-08-28
forum: Hardware
---

### Post by Jadzia Dax on 2011-08-28
Hi All, 

After reading many threads without luck, i decided to post this new one. 

I have been using ubuntu for some time now, but i am still a user :P so if you tell me to paste an output, please can you also tell me how to get it?

I had issues with video before, and i was able to get that fixed, so i am still using ubuntu 11.04 (i have weird issues once in a while, but i learned how to fix it).

Now i had to connect the computer using an hdmi cable, and after some configuration i was able to get it to work ok, both video and sound are working good, the only problem i have, is that it doesn't recognize the whole screen, i have some black borders that are not being used.

It is not a resolution issue, xrandr says it's on 1920x1080.  I had this same thing happening on windows (i rebooted to try this out) and i was able to get it fixed using ati catalyst drivers.  It made me overscan the area, and it got it fixed.  Now for ubuntu, i have no idea on how to do that.

I don't have ati drivers on this ubuntu, because they didn't work, so i am wondering if there is any way of getting this fixed with the generics drivers.

Thanks!!

PS: This is my xrandr output:  

> 
adzia@jadzia:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0*+   50.0     30.0     25.0     24.0  
   1776x1000      60.0 +   50.0  
   1600x1200      60.0  
   1680x1050      60.0     50.0  
   1400x1050      60.0     50.0  
   1280x1024      75.0     60.0     50.0  
   1440x900       59.9     50.0  
   1280x960       75.0     60.0     50.0  
   1920x540       60.1     50.0  
   1280x800       75.0     60.0     50.0  
   1152x864       75.0     60.0     50.0  
   1280x768       74.9     59.9     50.0  
   1280x720       60.0     50.0  
   1024x768       75.0     70.1     60.0     50.0  
   1152x648       60.0  
   800x600        72.2     75.0     70.0     60.3     56.2     50.0  
   720x576        50.0     25.0  
   720x480        59.9     50.0     30.0  
   640x480        75.0     72.8     60.0     50.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1920x540       60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  



---

### Post by gordintoronto on 2011-08-28
It might help if you said exactly what video card is in your computer, and exactly what brand and model of display is at the other end of the HDMI cable.

---

### Post by Jadzia Dax on 2011-08-28
Thanks!

Video card is: [B]Ati HD 4670 and the screen is P2370MS.
[/B]

---

### Post by gordintoronto on 2011-08-29
When you run System/Preferences/Monitors, what do you see?

(I don't see the same thing, because it puts me into the Nvidia configuration program.)

---

### Post by Jadzia Dax on 2011-08-29
Hi, 

It shows me the resolution on 1920x1080, so i think that is ok.


I was reading it is an overscan issue, but before i had another issue with ati drivers, so i don't have ATI drivers installed, i have the ones that come with linux, so all solutions that are with ATI drivers, do not really work for me. 

I think i will have to go back to ugly windows, but i hate to be missing so much of my screen.  Or maybe try fedora to see if i get the same thing happening. 

Kind of sux :(

Or maybe i will go back to 10.11 , i think 11.04 brought me many problems i didn't have before.

---

