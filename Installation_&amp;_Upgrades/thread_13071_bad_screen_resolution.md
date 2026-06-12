---
title: "bad screen resolution"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by gogodidi on 2005-01-28
Is there a way to change the screen resolution?

I ave used mandrake linux til now, so i could just go into the control panel. but on ubuntu, even with the desktop-->administration-->screen resolution, I can only get upto 1024x768, I used to have 1280x1024, any way to change this?

yaay(currently installing kde, took a while to get some permissions right...)

---

### Post by celloandy on 2005-01-28
Edit your /etc/X11/XF86Config-4 or /etc/X11/xorg.conf (whichever X server you use).  The first and most important change is to change your modelines in section "Screen," to add the option for 1280x1024, as follows:
```
SubSection "Display"
	Depth           24
	Modes           "1024x768" "800x600" "640x480"
EndSubSection
```
becomes
```
SubSection "Display"
	Depth           24
	Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
```
There will be a whole bunch of these "Display" subsections within the "Screen" section, with different values for depth, so just go ahead and change them all.

The other thing that needed tweaking on my install to get 1280x1024 was to change the allowable refresh rates in the "Monitor" section, which were initially really conservative.  On my monitor, this meant a change from
```
Section "Monitor"
	Identifier      "Generic Monitor"
	HorizSync       28-49
	VertRefresh     43-72
	Option          "DPMS"
EndSection
```
to
```
Section "Monitor"
	Identifier      "Generic Monitor"
	HorizSync       30-80
	VertRefresh     50-160
	Option          "DPMS"
EndSection
```
Your mileage may vary as far as refresh rates go, since each monitor has its own settings, so if you can, find out what the actual horizontal and vertical sync limitations of your monitor are, and modify the file accordingly.  In any case, I think these settings are somewhere around the minimum necessary for 1280x1024, so given that you've said that your hardware can support that, I doubt you'll have any problems.

Andrew

---

### Post by gogodidi on 2005-01-28
wow

i changed the code, I suspect i'll have to log out and in again, for it to take effect, but thanks.

---

