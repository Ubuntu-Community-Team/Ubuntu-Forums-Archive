---
title: "Disabling No synaptics Touchpad"
date: 2009-05-03
forum: Hardware
---

### Post by SkyPlooM on 2009-05-03
Hi,
I've tried to disable my touchpad sometimes in ubuntu 8.10 and now in 9.04. It's impossible.
I think is not a synaptics touchpad.

I've installed synaptics and I've the Touchpad options in System -> Preferences -> Touchpad. 
When I press it, I have this:
[I]GSynaptics can't run.
You need to configure the 'SHMConfig' variable to 'true' in filexorg.conf or XF86Config that GSynaptics uses[/I]
(It's not literal, I've ubuntu in spanish)

Well, I have this for **synclient TouchpadOff=1** in a terminal:
*Can't access shared memory area. SHMConfig disabled?*

Here is my /etc/X11/xorg.conf
> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionThere is nothing about touchpad.
It should be a touchpad section like this:

> [INDENT][I]**Section “InputDevice”**
** Identifier    “Synaptics Touchpad”**[B]
Driver        “synaptics”[/B][B]
Option        “SendCoreEvents”    “true”[/B][B]
Option        “Device”        “/dev/psaux”[/B][B]
Option        “Protocol”        “auto-dev”[/B][B]
Option        “HorizScrollDelta”    “0&#8243;[/B][B]
Option        “SHMConfig”        “true”[/B][B]
EndSection [/B][/I]        
[/INDENT]Some ideas?? Thanks.

Netbook: Point of view - Mobii
Ubuntu 9.04

---

### Post by FlyingBuzz on 2009-05-03
install gsynaptics and enable SHMconfig.
Actions to be performed are listed here
[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

### Post by pauna on 2009-05-03
You can either add the required touchpad InputDevice section to your xorg.conf, in which case you also need a ServerLayout section:

```

Section "ServerLayout"
  Identifier "Default Layout"
  Screen "Default Screen"
  InputDevice "Synaptics Touchpad"
EndSection

``` 

Besides, the InputDevice section should have the SHMConfig setting "On" instead of "true".

Alternatively you can say basically the same SHMConfig thing in the new /etc/hal/fdi/policy/shmconfig.fdi XML file as detailed in [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Whichever you feel more comfortable with.

---

### Post by SkyPlooM on 2009-05-03
I followed that manual on ubuntu 8.10 and I hadn't good results.
Now, in 9.04, is the same.

FlyingBuzz I've installed synaptics, I said on my first post, but nothing works

pauna I followed the manual again:

I haven't the touchpad section in mouse options
I did the Enable SHMConfig section, and nothing. The same error.
The xinput list said that my touchpad is:
  > "ImExPS/2 Generic Explorer Mouse"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1If I do what you say in xorg.conf, writing it like this:
> Section "Device"
     Identifier    "Configured Video Device"
 EndSection
 
 Section "Monitor"
     Identifier    "Configured Monitor"
 EndSection
 
 Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
 EndSection 

Section "ServerLayout"
  Identifier "Default Layout"
  Screen "Default Screen"
  InputDevice "Synaptics Touchpad"
EndSection

Section &#8220;InputDevice&#8221;
 Identifier    &#8220;Synaptics Touchpad&#8221;
Driver        &#8220;synaptics&#8221;
Option        &#8220;SendCoreEvents&#8221;    &#8220;true&#8221;
Option        &#8220;Device&#8221;        &#8220;/dev/psaux&#8221;
Option        &#8220;Protocol&#8221;        &#8220;auto-dev&#8221;
Option        &#8220;HorizScrollDelta&#8221;    &#8220;0&#8243;
Option        &#8220;SHMConfig&#8221;        &#8220;true&#8221;
EndSection        When I restart, I have ubuntu in low-grpahics mode and I had to select the reconfigure X mode.

(I restarted after every change)

Also the touchpad not works properly (in windows, it works). If you try to move it, it clicks what it wants and move in horizontal and vetical position, but not all around.

This is why I think that the touchpad is not a synaptic touchpad. I've readed a lot of differents ways to disable touchpad and no one works for me.

Thanks a lot.

---

### Post by mariner09 on 2009-05-03
Have you looked in your dmesg file to see what device is being recognized?

---

### Post by SkyPlooM on 2009-05-04
Hi,

>  dmesg | grep mouse
[   11.711568] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[   12.380170] mice: PS/2 mouse device common for all mice
[   20.328530] psmouse serio2: ID: 10 00 64<6>Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k

I have this with dmesg. (I did with the usb mouse disconnected)

Thanks.

---

### Post by SkyPlooM on 2009-05-04
I finished my ideas, and google finished its answers...some idea on what can I do??

The last idea is open the netbook, and disconnect the touchpad manually, if it's possible...

It's very disturbing the accidentally clicks on it...

Thanks.

---

### Post by pauna on 2009-05-04
From your xinputs output it looks like your device is a mouse, not a touchpad. In my xinputs output I have both. I don't know whether you pasted it wrong or if you have a real device recognition problem.

My working xorg.conf in its entirety:

```

Section "InputDevice"
	Identifier	"ETPS/2 Elantech Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"MaximumTapTime"	"200"
	Option		"MaximumDoubleTapTime"	"5"
	Option		"MaxTapMove"		"320"	
	Option		"ClickTime"		"50"
	Option		"VertTwoFingerScroll"	"1"
	Option		"VertScrollDelta"	"80"
	Option		"VertEdgeScroll"	"0"
	Option		"VScrollEmuOff"		"1"
	Option		"HorizEdgeScroll"	"0"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"On"
	Option		"TapButton3"		"2"
	Option		"TapButton2"		"3"	
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver	"ExplorerPS2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"ETPS/2 Elantech Touchpad"
	InputDevice	"Configured Mouse"
EndSection

```

---

### Post by SkyPlooM on 2009-05-04
Well, I don't know...the touchpad works well or not...it depends. Sometimes only works in horizontal or only in vertical and other times it clicks non stop on the Recycle bin (the right down corner)...I'm writing to Point of view support...

Some any idea??

Thanks a lot

---

### Post by SkyPlooM on 2009-05-09
Well, I finally found the solution following this manual:

[https://wiki.ubuntu.com/X/Config/Input#Dynamic%20Input%20Configuration%20with%20xinput](https://wiki.ubuntu.com/X/Config/Input#Dynamic%20Input%20Configuration%20with%20xinput)

Thanks a lot

---

