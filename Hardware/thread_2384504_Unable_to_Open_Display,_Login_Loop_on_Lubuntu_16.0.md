---
title: "Unable to Open Display, Login Loop on Lubuntu 16.04"
date: 2018-02-08
forum: Hardware
---

### Post by cobalt2 on 2018-02-08
My HDMI monitor was working fine until I connected a DVI monitor, to test it. The DVI monitor was working. Then I disconnected it and switched to the HDMI display, but there was no signal. I rebooted and disconnected the DVI display. Upon logging in, the screen went blank. Upon querying the display using xrandr it was showing a maximum resolution of 320x320, whereas the real maximum resolution is 1920x1080.

I resarted the computer with the hdmi and dvi displays connected with only the dvi display turned on. I logged in and everything was working fine. Then I switched to hdmi output the image emerged. On the next reboot the the display again went blank after logging in. I tried deleting .Xauthority and restoring it by entering:

> 
rm ~/.Xauthority
xauth generate :0 . trusted

And got this error:

> file: ~\.Xauthority does not exist
No protocol specified
[COLOR=#454545][FONT=&amp]xauth: (argv):1:  unable to open display ":0"[/FONT][/COLOR]

xauth failed to recreate .Xauthority, so I rebooted. Then I checked again and it was recreated. Apparently I’ve caused some damage in deleting .Xauthority becuase I'm no longer able to query the display. This is what happens when I try to query it:

> xrandr -d :0 -q
Invalid MIT-MAGIC-COOKIE-1 keyCan't open display :0
rm ~\.Xauthority
xauth generate :0 . trusted

 
Now I’m unable to login and bring up the desktop at all. Logging in to my account triggers a login loop. After logging in the screen blanks for a moment, returning to the greeter.

Ive tried restarting X server and lightdm, reinstalling lightdm and nouveau to no avail.

Specs:
Graphics: AMD RS780D [Radeon HD 3300]
Display: Dell SE2417HGR 24” monitor
Interface: HDMI

Any idea how to validate .Xauthority and gain access to the display again?

---

