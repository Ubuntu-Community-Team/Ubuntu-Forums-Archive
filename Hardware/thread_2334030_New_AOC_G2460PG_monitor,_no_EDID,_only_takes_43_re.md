---
title: "New AOC G2460PG monitor, no EDID, only takes 4:3 resolutions"
date: 2016-08-15
forum: Hardware
---

### Post by SanguineIllusion on 2016-08-15
I recently bought a 24" AOC G2460PG monitor. I mainly use it with a Windows 10 gaming PC which works great. I however have a work laptop and a personal laptop running Ubuntu that I've tried to run it on but it fails to do EDID detection and only gives me the options for 1024x768, 800x600, 640x480. The native resolution is 1920x1080. Some info about my setup:

Both laptops are model Thinkpad T440s. They have a mini display port and the monitor only outputs regular display port so I'm using a simple adapter. One laptop is running Ubuntu 14.04. The other was running 14.04 but is now running Ubuntu MATE 16.04, same issue. I dragged out an older Thinkpad with a full size displayport plug just to test it on ubuntu and the same thing happened, so it seems unlikely to be the adapter. All machines are using onboard video, but I know its capable of pushing 1920x1080 to an external monitor because day in and day out I use an old samsung with that resolution via a DVI to mini display port adapter. I've found several threads here for generating a modeline and feeding it to xrandr and then setting the monitor to it but any resolution over 1024x768 will just turn the monitor on standby and it will say that it lost the signal.

Is this a driver thing? I feel like if I got EDID working properly I'd be able to choose the right resolution. I don't really know where to go from here. I haven't contacted the manufacturer yet because I'm certain they'll take the first opportunity to say they don't support linux and drop my case.

---

### Post by CatKiller on 2016-08-16
It sounds like you're on the right track with the lack of EDID, which would allow the monitor to auto configure. It's possible to load EDID data from a file in xorg.conf. I believe there are utilities that will save the EDID data from the monitor to a file. It might be possible to boot into Windows, save that data, and then copy the file over to use in Linux.

Otherwise, my favoured solution is not to use a full modeline but to specify the appropriate horizontal and vertical frequency ranges in xorg.conf to keep much as possible automatic. That information tends to be relatively easy to come by. I'm a bit rusty on that, and I'm typing on a phone, but shout if you need help with that & I'll respond with more detail when I get the chance.

A quick look at the AOC website suggests that ```
HorizSync 30-160
VertRefresh 50-146
``` would be appropriate for that monitor.

The X log file is at /var/log/Xorg.0.log if you wanted to look at the specifics of why auto configure is failing. I had a monitor that reported incorrect EDID values, so I needed to tell X to ignore that.

---

### Post by SanguineIllusion on 2016-08-18
So the weird thing is I think the edid is possible to get with get-edid:

> sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 7
No EDID on bus 8
1 potential busses found: 6
128-byte EDID successfully retrieved from i2c bus 6
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "&#65533;"
	ModelName "&#65533;"
	VendorName "LGD"
	# Monitor Manufactured week 0 of 2013
	# EDID version 1.4
	# Digital Display
	DisplaySize 310 170
	Gamma 2.20
	Option "DPMS" "true"
	Modeline 	"Mode 0" 140.10 1920 1980 2016 2092 1080 1083 1088 1116 +hsync -vsync 
EndSection


Now, its kind of tricky since my laptop's display and the monitor are both 1920x1080 but I presume the first number in the modeline, 140.10 is the frequency and this is a 144hz monitor, whereas I doubt my laptop monitor is.

I'd prefer to keep this out of Xorg configs if I can help it because this monitor will not always be plugged in, and other monitors might. Seems like randr is more flexible there. Nevertheless, I don't have an Xorg.conf as I'm running ubuntu 16.04 which seems to give you a /usr/share/X11/xorg.conf.d folder, so I threw in a file 50-aoc-monitor.conf:

> 
Section "Monitor"
	Identifier " 
                     @"
	ModelName " 
                    @"
	VendorName "LGD"
	# Monitor Manufactured week 0 of 2013
	# EDID version 1.4
	# Digital Display
	DisplaySize 310 170
	Gamma 2.20
	Option "DPMS" "true"
	Modeline 	"Mode 0" 140.10 1920 1980 2016 2092 1080 1083 1088 1116 +hsync -vsync 
        HorizSync 30-160
        VertRefresh 50-146
EndSection


And I actually got no login screen and had to drop to a terminal and rename this file. Maybe something to do with the mangled identifier and model name? How does X11 know to associate it to my *external* monitor when there's 2 monitors at play?

Also, since get-edid seems to be able to find the edid, why can't randr?

---

### Post by SanguineIllusion on 2016-08-18
Oh and I should mention I don't get anything interesting from Xorg.0.log when I tail it and then unplug and plug in the misbehaving monitor:

[   778.691] (II) intel(0): resizing framebuffer to 1920x1080
[   783.062] (II) intel(0): resizing framebuffer to 2944x1080
[   783.081] (II) intel(0): switch to mode 1024x768@60.0 on DP1 using pipe 1, position (1920, 0), rotation normal, reflection none

---

