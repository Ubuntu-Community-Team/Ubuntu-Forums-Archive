---
title: "Kitty broke my hardware"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Rotarychainsaw on 2007-11-26
Ok, I'm having a weird problem. My cat knocked my old dreamcast off the top of my computer. It went down the back by all the wires. At that time the computer locked up and would not reboot, it would only give me a bunch of bios beeps.
I had to leave for thanksgiving before I got to try fixing it. When I got back here, I pressed in my video card again to make sure it didn't get moved. and booted it up. It booted, but now everything is very unstable. If I use compiz, random programs crash at random times. 
I have taken off the small overclock that I had going, put everything back to defaults, and it is still crashing and stuff. 

Is there anyway to find out what is going on? Logs are blank. I'm gonna run memtest overnight and see what that says.

Its weird because this wasn't a really big jolt or anything, so I don't think anything really got hit loose, possibly the video card, but thats it. I'm running nautilus right now and it seems to be a little more stable. We'll see.

---

### Post by Rotarychainsaw on 2007-11-26
memtest came up clean. Memory is set to an odd timing in memtest that I cant seem to change. ddr259 or something. Very unstable on the desktop. even in metacity.

---

### Post by Rotarychainsaw on 2007-11-26
Nov 26 11:09:11 localhost kernel: [   94.740000] swap_free: Bad swap file entry 08000000
Nov 26 11:09:11 localhost kernel: [   94.740000] Eeek! page_mapcount(page) went negative! (-1)

Those are the last things in my kernel log before a reset. I wonder what that means... Still passing memtest all day.

---

