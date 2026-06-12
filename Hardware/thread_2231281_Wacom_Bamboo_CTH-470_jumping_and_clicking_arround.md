---
title: "Wacom Bamboo CTH-470 jumping and clicking arround"
date: 2014-06-24
forum: Hardware
---

### Post by skipx on 2014-06-24
Hi,
After almost a year of accepting and sometimes trying hard to solve I better ask my question here! 
I got this Wacom Bamboo CTH-470 tablet which is really nice. Until after using it for like 5 minutes. Then the cursor starts having a life on its own. It jumps randomly over the screen and also does right- and left clicking on its own. Its really happy and free. Today it even kicked out my BT keyboard somehow (until I brought it back of course). 

So I must miss some setting here and there. I would be great if someone could point me some direction!
I'll try to give enough infor now :)

Thanks!

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

$ uname -a
Linux abort-mbp 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:23 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ lsusb |grep Wacom
Bus 003 Device 004: ID 056a:00de Wacom Co., Ltd

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                 	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen stylus        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen eraser        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger touch      	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger pad        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Apple Computer, Inc. IR Receiver        	id=9	[slave  keyboard (3)]
    &#8627; Apple, Inc. Apple Internal Keyboard / Trackpad	id=10	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=12	[slave  keyboard (3)]
    &#8627; Admin&#8217;s keyboard                      	id=17	[slave  keyboard (3)]

$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf 
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
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

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
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

### Post by robjuffermans on 2014-11-22
same problem!

Tried other laptop with Fedora 21, but no change.

---

