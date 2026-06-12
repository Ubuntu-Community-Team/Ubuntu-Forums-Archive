---
title: "Ubuntu 11.1 on Toshiba m700 - Touch Screen Problem"
date: 2012-01-10
forum: Hardware
---

### Post by FGazerro on 2012-01-10
Hello, 

I recently bought a refurbished Toshiba M700 tablet PC. I installed Ubuntu. The stylus and eraser worked out of the box, however, I've experienced other problems: 

(1) The screen will not autorotate when I rotate the monitor. 

(2) There seems to be no touch screen support and Ubuntu doesn't seem to recognize the tablet itself. When I run xinput --list, only the stylus and erasers are listed.

Most of the discussion in the forums on the subject pertains to older versions of Ubuntu (7.1-9.1). Any help would be appreciated. 


Here are the results of xinput list:

Virtual core pointer            id=2 [master  pointer  (3)]
&#8627; Virtual core XTEST pointer    id=4 [slave  pointer  (2)]
&#8627; PS/2 Mouse                    id=11 [slave  pointer  (2)]
&#8627; AlpsPS/2 ALPS GlidePoint      id=12 [slave   pointer  (2)]
&#8627; Serial Wacom Tablet stylus    id=13 [slave  pointer  (2)]
&#8627; Serial Wacom Tablet eraser    id=15 [slave  pointer  (2)]

Virtual core keyboard           id=3 [master keyboard (2)]
&#8627; Virtual core XTEST keyboard   id=5 [slave  keyboard (3)]
&#8627; Power Button                  id=6 [slave  keyboard (3)]
&#8627; Video Bus                     id=7 [slave  keyboard (3)]
&#8627; Power Button                  id=8 [slave  keyboard (3)]
&#8627; Chicony USB 2.0 Camera        id=9 [slave  keyboard (3)]
&#8627; AT Translated Set 2 keyboard  id=10 [slave  keyboard (3)]
&#8627; Toshiba input device          id=14 [slave  keyboard (3)]



Here is my 50-wacom.conf file:

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WALTOP|WACOM|Hanwang|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

---

