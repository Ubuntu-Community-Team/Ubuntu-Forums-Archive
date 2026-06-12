---
title: "sensors.applet killed my CPU fan"
date: 2009-02-17
forum: Hardware
---

### Post by Threk on 2009-02-17
I've got an old Thinkpad A22 I normally use as a MythTV frontend.

I recently had a very large batch of video clips I wanted to convert and decided to do it on there instead of on my main comp. 

After converting a few files it overheated. I installed lm-sensors to watch the temp while the conversion was running, and changed my script to pause after each one if the temp was too high. It slowed things down, but otherwise everything was fine, until I decided I wanted a better way to see the temp. 

When I installed the Gnome panel sensors.applet, I immediately noticed that the sensors command no longer returned a bunch of sensors, now it's just the CPU, but I didn't worry too much. It also seemed to be heating up faster, but at first I assumed it was just because I was running the full Gnome desktop instead of just Mythfrontend. When the rapid heating continued after I logged out of the Desktop and back to just the frontend, I checked the CPU fan and noticed it wasn't running. When I rebooted to a live CD the fan worked fine, but now it dies as soon as Ubuntu starts to load off the hard drive.

I tried uninstalling the applet, re-installing lm-sensors, and running sensors-detect, but sensors still only returns the CPU temp now, and the fan stays off.

There doesn't seem to be a setting in the BIOS to force the fan on. Can someone help me figure out how to turn the fan back on?

Thanks in advance

---

### Post by Threk on 2009-02-18
Bueller?

---

