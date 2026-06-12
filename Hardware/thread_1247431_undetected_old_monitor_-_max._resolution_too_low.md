---
title: "undetected old monitor - max. resolution too low"
date: 2009-08-22
forum: Hardware
---

### Post by joelunchbox on 2009-08-22
I just replaced an old computer with a new-ish one (P4 3.2 Ghz)  and installed Jaunty. The maximum allowed screen resolution is 800x600 with this new system, but I would really like to get to 1024x768 which I had before. I know this is a problem with the auto-detection of my monitor, which is an old (12 yrs) ViewSonic 29GA (29”) CRT. My video card is a brand-new ATI Rage 128 Pro 32MB PCI.
 

 I've been reading the forums but I'm just getting confused. The threads all seem to be about dual monitor or unsupported video card issues.
 

 I've read this, which was helpful for understanding what is going on:
 [https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions)
 

 my xrandr output is:
 

 Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600 
 default connected 800x600+0+0 0mm x 0mm 
    800x600        60.0*    56.0   
    640x480        60.0   
    400x300        60.0     56.0   
    320x240        60.0
 

 Figuring out how exactly to modify my xorg.conf file eludes me. I've been using Ubuntu since Hoary, but when it comes to the terminal, I've always been a copy-and-paste noob. Searching the forums has helped me with issues in the past, but this time I'm running stuck. Thanks in advance to anyone who can help!

---

