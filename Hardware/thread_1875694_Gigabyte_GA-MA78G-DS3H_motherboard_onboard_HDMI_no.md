---
title: "Gigabyte GA-MA78G-DS3H motherboard onboard HDMI not working"
date: 2011-11-05
forum: Hardware
---

### Post by axhart on 2011-11-05
I apologize in advance for my lack of knowledge, I'm relatively new to Ubuntu and my computer skills are lacking, to say the least.

I've recently switched from my video card back to the onboard video of my Gigabyte GA-MA78G-DS3H, so I could make use of its HDMI port. I can get to the boot screen, but before Ubuntu loads I lose the signal for HDMI.  

When I use the VGA connection instead, I have no issues.  I wanted to try booting in safe mode, but my keyboard refuses to work at the screen which allows me to select how I want to run Ubuntu (I can get to BIOS with the keyboard so I'm not sure what the issue is there).  

Any idea as to what I'm doing wrong?  Again, I apologize for my ignorance in these matters.

---

### Post by axhart on 2011-11-05
So I looked around a bit more and found this thread with a solution:

[http://ubuntuforums.org/showthread.php?t=1333717](http://ubuntuforums.org/showthread.php?t=1333717)

I changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to 

GRUB_CMDLINE_LINUX_DEFAULT=""

but it hasn't made a difference.

---

