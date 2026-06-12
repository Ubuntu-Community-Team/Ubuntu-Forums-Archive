---
title: "mouse skipping/poor tracking after sleep"
date: 2009-10-30
forum: Hardware
---

### Post by Paul McDermott on 2009-10-30
On both Ubunto 9.04 and now 9.10 my USB wired mouse (Microsoft Comfort Optical Mouse 3000) works fine when the computer starts or is restarted, but once the computer goes to sleep, when it wakes up the mouse doesn't track smoothly and instead skips.  The computer is an Acer Aspire 5517.  This problem did not occur when the laptop ran windows, and it does not occur on Fedora 11.  The problem also occurs when i try another mouse (an apple mouse).  Also, the mouse pad/track surface I do not believe is the issue.

Thanks in advance for any advice or tips.

-Paul

---

### Post by tuco penguin on 2009-11-02
I have the same problem with my Acer Aspire 5739G laptop.  After the computer goes to sleep mode and wakes back up, the pointer motion when using a USB mouse is sometimes a bit erratic.  I use a Logitech Premium Optical Wheel mouse, and a Targus retractable-cord travel mouse with same results.  I'm pretty sure it is not a mouse or hardware issue--no problems when booting to Windows Vista.  A little additional info:

1.  Like the OP, mouse works fine on boot/reboot.

2.  The touchpad behavior does not appear to be affected, just the USB mouse.

3.  Opening the mouse preferences dialog and changing a setting appears to restore the good behavior when the mouse is being skippy or erratic.

4.  I have, on a few occasions, had all input devices (keyboard, mouse, touchpad) lock up completely requiring a reboot with the power button.  I don't know if this could be related or not.  I have not figured out how to reproduce this problem, though.  I believe it is related to the switching of power management states because it only ever happens when I leave the computer unattended for some time, not while I'm actively using it.

I wonder if USB controller software is running without proper scheduling priority?  Perhaps some adjustments with "nice" command would help?  This is on the fringe of my Linux understanding, but I certainly don't mind expanding my frontiers--that's why I'm here!

---

### Post by Paul McDermott on 2009-11-05
tuco penguin,
What mouse settings did you adjust that returned the mouse back to normal?  I tried adjusting the acceleration and sensitivity, but unfortunately it didn't cure the problem.  I will have to look into the "nice" command, but my intro to linux book is unfortunately on backorder. :(  Also, do you notice any internet surfing slowdown after sleep?  I seem to and I mention it since my mouse problem also occurs after sleep.  If you or anyone else has any tips or suggestions, I would appreciate it.  Thanks in advance.  
-Paul

---

