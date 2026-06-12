---
title: "HP Desktop fan never stops"
date: 2010-04-16
forum: Hardware
---

### Post by hosseink on 2010-04-16
Hi there everybody,
I am a new Ubuntu user, and I've just installed it on my new 64-bit HP desktop computer.
The computer was originally shipped with Windows 7.
I managed to modify the hard disk and install Ubuntu as the second OS.
The system runs a noisy fun when it boots, and when Windows 7 comes up the fan is automatically turned off.
However when Ubuntu starts, the fan continues to work endlessly.
I was trying to find a solution to my problem in the previous posts, but it seems that the opposite problem (the fan does not work) is more likely.
Therefore I am asking for your help to force Ubuntu to control the fan.

Regards,;-)

---

### Post by hosseink on 2010-05-20
Hi to all who didn't replied me,

I finally was able to diagnose and resolve the problem, so I put it here for those who would face the same problem.

The problem was with the Graphics Card fan which was not stopped by the Ubuntu graphical driver. So I found the appropriate driver from the NVIDIA website and installed it. It required me to kill the X server.
When I restarted my computer the magic was revealed: no more noise.

I just wanted to share my happy moment with you.

Regards,:grin:

---

### Post by pkbyron on 2010-05-21
Thanks for the tip [hosseink]("http://ubuntuforums.org/member.php?u=1055096").

I have just installed 10.04, and have exactly the same issue - FAN always running.

After reading your post I ran a Hardware Drivers scan and it installed a new driver.  But alas it didn't work on restart and went into the basic mode.
I downloaded and installed it manually too and it hasn't worked.  

Just wanted to ask which Card  you had in your HP?
I have a HP Desktop Pavilion p6120a with a NVIDIA GeForce GT 220.

Its frustrating as the box is dual boot - with Vista, and its quite as a mouse and crystal clear on the widescreen.

cheers

pkbyron

---

