---
title: "Monoprice/Huion Graphics Tablet Display Config issue..."
date: 2014-09-18
forum: Hardware
---

### Post by renegade-traceur on 2014-09-18
Hi folks, 
  I recently got a HUION GT-190/Monoprice ("UC-Logic: 006E" in the lsusb) command. The tablet functions of the display  seem to work natively with the kernel. However, the tablet display is 16in X 10in (1400px X 900px), but the tablet pen only works in the top corner of the display like its an 8in x 5in (or 700px by 450px). Is there a configuration file like the old xorg.conf where I can change the dimensions of the graphics tablet active area?

Any help is appreciated and I'm sure more than a few people may need an answer to this question?

Note: I am not using dual displays yet. 

Ubuntu 14.04 on AMD PHENOM x6 3.4ghz with nvidia 690gtx

---

### Post by renegade-traceur on 2014-09-18
I was able to make some progress by adding the following to the 50-wacom.conf file in /usr/share/X11/xorg.conf.d/

```

# HUION GT-190 TABLET DISPLAY
Section "InputClass"
	Identifier "Tablet Monitor"
	MatchProduct "HID 256c:006e|Tablet Monitor"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
	Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"  
EndSection

```

The problem I'm having now is finding the correct dimensions for TopX,Y and BottomX,Y.  I really wish the old wizardpen repository was working so I could use the calibrate tool. Anyone have any idea for the active area of a 19" pen display?

---

### Post by marcus26 on 2014-10-04
same problem here. anybody, please?

---

