---
title: "Monitor display off-center anytime the display 'refreshes'"
date: 2011-09-09
forum: Hardware
---

### Post by 10panxianshi on 2011-09-09
Hey everyone...

i'm new to this so please bear with me.  I used the search function on the forums to try and find an answer and have tried a few different things.  I've been referring to the [https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution) page but have yet to have any luck.  if you have any idea of how to help i'd appreciate your know-how.  

My problem is this:

I have Ubuntu 10.10 (maverick)  on a previously Windows XP Hewlett Packard computer.   I have had difficulty getting the monitor to display a correct image.  I can reset it by changing the resolution from the 'monitor' menu but after the screen 'refreshes' (ex:  starting a video, or the computer going to sleep) the display will come back off center and the mouse is not responding to the same place the image is displayed.   I hope that makes sense.  anyways the way i have been solving this problem is to go back into the monitor settings and switch it to a different resolution, then hit 'revert changes' after the screen refreshes and for some crazy reason it will display correctly again... until the screen for whatever reason refreshes itself.   needless to say its putting me to the brink of insanity. 

other information that might be helpful:

the monitor is the one that came with the computer, so ideally it should register correctly right?  the monitor is called "HP pavilion vf51"  but i have also tried to use my Vizio LCD tv and it has the exact same problem. 

the graphics card is listed as "nVidia corp NV18 [GeForce4 MX -nForce GPU (rev a3)" I have updated the drivers today and it didn't fix the problem.  

alright.... I also made a short video and posted it to youtube trying to document the problem in action if that would help... it was shot with my phone so it may not be the best quality but I hope it gives the idea.  

[http://www.youtube.com/watch?v=ATgLpLtHOqc](http://www.youtube.com/watch?v=ATgLpLtHOqc)

thank you in advance for your assistance.   if you do choose to reply and help me just realize I'm verrrrrrry new to linux and pretty novice in my computer skills in general.  If you give me detailed instructions I can follow them but keep in mind i'm pretty n00b.  

Thanks!

10panxianshi

---

### Post by newbasford on 2011-11-14
I have this same problem too!

Please somebody help!

Thank you,

(elonex lcd monitor 1024 x 768)

---

### Post by newbasford on 2011-11-14
I have now solved this problem by installing the proprietary hardware driver for the graphics:

go to system>administration>hardware drivers

the system scans for its drivers,

then you will be offered to install the NVIDIA accellerated graphics driver (version 96)

install it, then restart your computer

should be okay now.

NB: the monitor option under 'system>preferences' now redirects to another tool for making adjustments, but it works fine.

---

