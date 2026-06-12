---
title: "Incorrect resolution on primary (eee pc) monitor, xrandr offsets incorrectly"
date: 2012-02-02
forum: Hardware
---

### Post by jywarren on 2012-02-02
I replaced a broken 1024x600 display on my 11.10-running EEE PC, and the new monitor does not seem to offer a native 1024x600 display resolution, instead using 1024x768 and running over off the bottom of the screen. No problem, I ran the following commands in xrandr:

```
xrandr --output LVDS1 --newmode "1024x600_60.00"  48.96  1024 1064 1168 1312  600 601 604 622  -HSync +Vsync

xrandr --addmode LVDS1 1024x600_60.00

xrandr --output LVDS1 --mode 1024x600_60.00
```

But for some reason, the x600 display is offset by approx 200 pixels from the top of the hardware monitor, i.e. i get a black band at the top and the bottom runs off the edge so I can't see it. I tried messing with the "pos" flag, but it seems to have no effect:

```
xrandr --output LVDS1 --mode 1024x600_60.00 --pos 0x100
```

Not to mention, even if I did get the pos flag working, could I really give it a negative number, like "--pos 0x-200" ?

I also tried messing with the "scaling mode" hoping that it was set to something like "Center" and was positioning the 1024x600 screen vertically centered on what it thinks is a 1024x768 screen. I.E.:

```
xrandr --output LVDS1 --set "scaling mode" "Full aspect"
```

Anyways that didn't work either, with any of the available options. I'd really appreciate some suggestions!

---

### Post by jywarren on 2012-04-29
Well, for the sake of thoroughness, I found why the --pos flag wasn't working; if there is only one display, xrandr keeps it at 0x0 no matter what. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=512919](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=512919)

Still no solution on the incorrect screen size. Bummer.

---

### Post by jywarren on 2012-04-30
Just taking good notes here; I may try submitting it to the xorg forums/issuetracker/whatever:

Others with this problem have found different solutions: [hardware settings on the monitor]("http://ubuntuforums.org/showthread.php?t=1641066") (mine is built in, so I can't reconfigure it), [briefly changing resolution in the Displays panel]("http://ubuntuforums.org/showthread.php?t=1458283") (didn't work), and a lot of exploration of similar issues here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731) and here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/48289](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/48289)

Notes:

* I upgraded to 12.04 with no improvement
* I created an xorg.conf and hard-set the driver as "vesa", "fbdev" and "intel" and rebooted each time, they all show the same problem
* I added a manual Modeline etc to the xorg.conf ([https://gist.github.com/2558751](https://gist.github.com/2558751)) and used xvidtune to offset it upwards, to no effect, though /var/log/xorg.0.log shows that the custom modeline is being read and used.

* Xorg.0.log excerpt: [https://gist.github.com/2558830](https://gist.github.com/2558830)
* output of ddcprobe: [https://gist.github.com/2558837](https://gist.github.com/2558837)

This last output is concerning as it does not display 1024x600 resolution at all - which must be why xorg.conf changes and xrandr are "faking it" by displaying a vertically-centered 600px-tall screen on what it thinks is a 1024x768 screen. Buh.

And now:

* output from "get-edid" command: [https://gist.github.com/2558975](https://gist.github.com/2558975) -- and at this bug, they are just saying to remove the xorg.conf to see if X just "figures it out": [https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994)

---

### Post by jywarren on 2012-04-30
Now i'm getting an error message when i reboot: 

**Could not apply the stored configuration for monitors**


none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)

**Update:** OK, after removing the xorg.conf and ~/.config/monitors.xml files, the above warning disappears. I then tried to force an extra resolution before X even loads, using a kernel parameter in Grub2 -- i held down shift after the initial Asus load screen, and added "video=1024x600" to the end of the "quiet splash" line. It didn't work (also the "vga=ask" parameter is deprecated, so that didn't work either).

Wow this is quite the intractable bug. Still looking into why EDID fails and how to add the correct resolution there.

---

### Post by jywarren on 2012-05-02
OK, folks at tinycore ([http://forum.tinycorelinux.net/index.php/topic,6871.15.html?PHPSESSID=34vjhucenruckrkmh92nu62hj3](http://forum.tinycorelinux.net/index.php/topic,6871.15.html?PHPSESSID=34vjhucenruckrkmh92nu62hj3)) are struggling with a similar problem and suggest a kernel mode setting (KMS) like this (similar to the GRUB technique at boot, above):

vga=577

They also suggest adding the following lines to xorg.conf in Section "Monitor": 

	HorizSync 31.5 - 37.9
	VertRefresh 50.0 - 70.0
	DisplaySize 195 113

and in SubSection "Display":

		Virtual 1024 600

Trying a few of these ideas now.

**Update:** Nope. Next, reading this bug on EDID failures: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

---

### Post by Sunships on 2012-05-24
Any luck with correcting the offset display?

---

### Post by jywarren on 2012-06-07
Just fixed this finally last night. It was the LVDS cable itself, which must've been damaged. Sad, but happy after all.

---

