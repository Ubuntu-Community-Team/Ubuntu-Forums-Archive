---
title: "ViewSonic VE155 Support"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by bb002 on 2005-10-05
I recently replaced Mandriva Linux 2005LE with Ubuntu 5.04 on my desktop recently, only to discover that I could not use any resolution other than 640X480 even after forcing the xserver to 1024X768 in /etc/X11/xorg.conf. At first i thought it was the video card drivers. I checked what drivers the xserver was using. It was using the generic "ati" drivers like all the faqs say it should for my gfx card. Next idea was since Mandriva worked fine with my hardware i'd see what it's xorg.conf looked like.
I switched the hdd with a spare and installed mandriva on it. checked the xorg config and discovered that the graphics driver was the same generic "ati". I then copied the xorg.conf to a jumpdrive and then switched back to the ubuntu hdd and noticed that ubuntu was missing the following lines for the ViewSonic VE155 Flat Panel Monitor in the xorg.conf:
```

HorizSync 31.5-48.5
VertRefresh 40-70

```
Once I added these lines to the /etc/X11/xorg.conf file the xserver finally worked in the 1024X768 resolution.
Now I was wondering where i can submit this info for it to be incoporated into ubuntu, so noone else will have such a problem with this monitor in the future.

---

### Post by bb002 on 2006-10-29
I have received a pm looking for some help so here are the instructions on how to make the changes to your xorg.conf

first you need to look up your monitor's vertical and horizonal refresh rates at it's manufacturer's website.

next, you'll need to open up a terminal by going to the gnome menu -> applications -> accessories -> terminal
now type in ```
sudo gedit /etc/X11/xorg.conf
``` click the find button and type in "monitor". keep clicking find until you find a section similar to the one below.
```
Section "Monitor"
	Identifier	"monitor"
	Option		"DPMS"
EndSection
```
add the following lines to the end of the monitor section, if the lines exist already change them.
Replace the numbers after HorizSync with the horizonal refresh rate found at the manufacturer's website. Do the same with VertRefresh but using the vertical refresh rate numbers this time. Note that the two numbers on each line **MUST** be separated with a dash. Separating them with anything else will produce an error and prevent X from starting.
```
HorizSync 31.5-48.5
VertRefresh 40-70
```
now your monitor section should look something line the one below
```
Section "Monitor"
	Identifier	"monitor"
	Option		"DPMS"
	HorizSync 31.5-48.5
	VertRefresh 40-70
EndSection
```

Save the file and close gedit.
now reboot. Ubuntu should properly set itself to the proper resolution. You can check by going to the gnome menu -> system -> preferences -> screen resolution. this is also where you can change your screen resolution.

---

