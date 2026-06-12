---
title: "Ubuntu not relinquishing control? (touchpad tap)"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by spdiscus on 2005-10-12
With both 5.04 and 5.10, when I **reboot** to Windows XP SP2, the tap functionality of my touchpad doesn't work. 
When I **halt and manually power back on to boot** to Windows XP SP2, the touchpad functions correctly. 

So, is it possible that Ubuntu doesn't let go of some sort of mouse module, and it takes a complete power-down for XP to grab full mouse control?

Running:
Dell Inspiron laptop - XP on first half of HDD, BB on second half of HDD.
GRUB loader, defaulting to BB.

Searching just came up with run-time Ubuntu tap issues. My issue is actually while running Windows.
Thanks.

---

### Post by audax321 on 2005-10-12
I'm not sure exactly what the problem is and can't really help you on this. But I do know of a similar problem with a version of the Microsoft Intellimouse where if you try to move the mouse and scroll at the same time in Linux, it doesn't work. BUT, if you boot into Windows first and then boot into Linux without powering off, moving the mouse and scrolling in the window will begin to work. As soon as you power off and boot into Linux, you lose the move and scroll funcitonality and have to go back into Windows (without a power off) to activate it again. Maybe this is similar??? Although I kind of expect that from Microsoft, it's kind of weird your having a problem like this with Linux... :confused:  

You might want to post who made your touchpad as well. I have a Synaptics on my laptop and don't have any issues at all. Also post the InputDevice sections of your xorg.conf.

---

