---
title: "Problem with Monitor, Video Card, or Something Else?"
date: 2011-02-19
forum: Hardware
---

### Post by lordofinsanity on 2011-02-19
Alright, haven't had too much trouble running my Ubuntu system for the last while, but found that the default monitor settings of 800X600 or 640x480 weren't to my liking. That said, I've set it up to be 1024x768, a reasonable setting considering I've always used that setup.

Today I experienced a weird crash that left me with a black monitor and three blue lines across the top part of the display. While this occurred, I also noted that the keyboard lights (num-lock, caps-lock) were flashing as the system does on boot. I restarted the system and once it booted everything seemed to be fine. I set the display once again with a short script I made to change the screen configuration and proceeded to continue working. After a half hour or so, the screen went black again, only this time there was a single cursor line at the top and the key lights were again flashing. No attempt to reboot worked and it did this for a while before I hard-booted the system.

I'm currently running an HP Pavilion a210n with a CTX monitor. Ubuntu is at version 9.10 and the RAM is 256 with a 2.5GHz processor. I'm not sure whether this might be a monitor issue, something with the video card, or something else, but would like your thoughts on the matter.

Let me know if I need to include more information or obtain other configuration settings as I currently don't have another system to work with.

Thank you. :)

---

### Post by jerrrys on 2011-02-19
the flashing lights is kernel panic.  reboot and when grub boot comes up (or make grub come up at boot) and drop back one kernel and see what happens

---

