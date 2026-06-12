---
title: "Need help with Trackpoint on X200."
date: 2009-11-02
forum: Hardware
---

### Post by SGFHK321 on 2009-11-02
This is really getting on my nerves (among other issues with 9.10) and I am on the verge of switching back to Windows.

So my trackpoint did not work "out of the box".  Thats ok.  I tried editing that fdi file, did not work.  I tried installing gpointing-device-settings, did not work.  I tried using these commands in terminal:
> xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Y Axis" 8 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation X Axis" 8 6 7

Works brilliantly.  So all I need to do is to put these commands in my startup script so to spare myself the inconvenience of having to do this on every boot.

Thats when the frustration hit me.

I put those lines in /etc/rc.local.  No effect.  I changed the execution bits to make sure the script is executable.  No effect.  No matter what I do.  The system just won't load the damn script!  Is there some other secret with linux that I need to know (like bash script)?  How do you execute console command in bash script, if this question makes sense?

Help much needed and appreciated.

---

