---
title: "synaptics touchpad middle-click issues/bug"
date: 2010-10-28
forum: Hardware
---

### Post by Mad_Gouki on 2010-10-28
I just did a fresh install of 10.10 the other day on my laptop, and it works great except for a strange problem with the touchpad (I think).

Middle click seems to randomly trigger when I click the mouse click button.  When I switch tabs in firefox it will sometimes close them, and sometimes when I click a link it copies it and then clicking on a text box will paste it, so it is without a doubt some weird middle click behavior.  I even tried disabling tap clicks on the touchpad and it still happens.

Is there another driver I can use, or a way to configure the way the buttons work?  I'm not afraid to go into some confusing seeming configuration files or anything, but I really have no idea where to even start looking to fix this.  What driver/config does ubuntu use for touchpads now?

Any help would be appreciated, thanks!

edit: whoops, I have 10.10, not 10.04.

---

### Post by jflaming on 2010-11-01
I am having the exact same issue.  I have searched through lots of bug reports and other posts, but they tend to be about the buttonless trackpads. 
This issue started effecting when I upgrade to 10.10.  I have tried a full clean reinstall.  The touchpad works fine on older versions via live CD.  I also do not have the problem when using an external mouse.  I have disable touchpad clicking, but no help.  
Occasionally when clicking a link in a browser, multiple copies will open.  When clicking a tab, the tab will sometimes close instead of focusing.  In apps, sometimes old highlighted text will be inserted when I click somewhere in a text document to move the cursor.
Hopefully someone else has some hints?

---

### Post by nh7o_hi on 2010-11-02
Use xinput to change the touchpad properties

man xinput
xinput --list     for device id's
xinput --list-props device        for properties of the device
xinput --set-props device prop value     to set the property

There are other posts about xinput. q.v.

---

### Post by jflaming on 2010-11-02
I looked through the other posts, and they mostly seem to be about multitouch or issues with touchpads without hardware buttons.  My touchpad has hardware buttons (which is what my problem is happening with, not the touchpad itself).  

I have two devices that seem relevant in xinputs.  Anyone see anything problematic in this?  

Device 'eGalax INC. USB TouchController':
	Device Enabled (117):	1
	Coordinate Transformation Matrix (119):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (236):	0
	Device Accel Constant Deceleration (237):	1.000000
	Device Accel Adaptive Deceleration (238):	1.000000
	Device Accel Velocity Scaling (239):	10.000000
	Evdev Reopen Attempts (234):	10
	Evdev Axis Inversion (240):	0, 0
	Evdev Axis Calibration (241):	<no items>
	Evdev Axes Swap (242):	0
	Axis Labels (243):	"Abs X" (253), "Abs Y" (254), "Abs Z" (255), "Abs Rotary X" (256)
	Button Labels (244):	"Button Left" (120), "Button Unknown" (235), "Button Right" (122), "Button Wheel Up" (123), "Button Wheel Down" (124)
	Evdev Middle Button Emulation (245):	2
	Evdev Middle Button Timeout (246):	50
	Evdev Wheel Emulation (247):	0
	Evdev Wheel Emulation Axes (248):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (249):	10
	Evdev Wheel Emulation Timeout (250):	200
	Evdev Wheel Emulation Button (251):	4
	Evdev Drag Lock Buttons (252):	0


Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (117):	1
	Coordinate Transformation Matrix (119):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (236):	0
	Device Accel Constant Deceleration (237):	1.000000
	Device Accel Adaptive Deceleration (238):	1.000000
	Device Accel Velocity Scaling (239):	10.000000
	Synaptics Edges (257):	1752, 5192, 1620, 4236
	Synaptics Finger (258):	24, 29, 255
	Synaptics Tap Time (259):	180
	Synaptics Tap Move (260):	221
	Synaptics Tap Durations (261):	180, 180, 100
	Synaptics Tap FastTap (262):	0
	Synaptics Middle Button Timeout (263):	75
	Synaptics Two-Finger Pressure (264):	280
	Synaptics Two-Finger Width (265):	7
	Synaptics Scrolling Distance (266):	100, 100
	Synaptics Edge Scrolling (267):	1, 0, 0
	Synaptics Two-Finger Scrolling (268):	0, 0
	Synaptics Move Speed (269):	0.400000, 0.700000, 0.009952, 40.000000
	Synaptics Edge Motion Pressure (270):	29, 159
	Synaptics Edge Motion Speed (271):	1, 401
	Synaptics Edge Motion Always (272):	0
	Synaptics Button Scrolling (273):	1, 1
	Synaptics Button Scrolling Repeat (274):	1, 1
	Synaptics Button Scrolling Time (275):	100
	Synaptics Off (276):	1
	Synaptics Guestmouse Off (277):	0
	Synaptics Locked Drags (278):	0
	Synaptics Locked Drags Timeout (279):	5000
	Synaptics Tap Action (280):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (281):	1, 1, 2
	Synaptics Circular Scrolling (282):	0
	Synaptics Circular Scrolling Distance (283):	0.100000
	Synaptics Circular Scrolling Trigger (284):	0
	Synaptics Circular Pad (285):	0
	Synaptics Palm Detection (286):	0
	Synaptics Palm Dimensions (287):	10, 199
	Synaptics Coasting Speed (288):	0.000000
	Synaptics Pressure Motion (289):	29, 159
	Synaptics Pressure Motion Factor (290):	1.000000, 1.000000
	Synaptics Grab Event Device (291):	1
	Synaptics Gestures (292):	1
	Synaptics Capabilities (293):	1, 0, 1, 1, 1
	Synaptics Pad Resolution (294):	135, 79
	Synaptics Area (295):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (296):	0

---

### Post by jflaming on 2010-11-02
Hey Mad, try this... I tried this command:
xinput --test 14 > testmouse.txt
and then used my computer for a while.  When I experienced a weird clicking issue, I went back to the terminal and ctrl-c killed it.  The log file shows:
motion a[0]=4386 a[1]=1550 
button press   2 
button release 2 

so when I pressed the left touchpad button, xinput was logging a middle-click.  

I have repeated this several times.  I'm not sure why sometimes the left click is button 1, and sometimes it is recording a button 2.  It only started happening after update to 10.10. 

As a workaround, I am trying to figure out if I can disable button 2 on this device (without killing it on my external mouse).  I'm new to xinput, so I am struggling a bit to figure out how to do it.

---

### Post by jflaming on 2010-11-02
I tried modifying the values for device to prevent button 2 (middle click), following instructions from here:
[http://blog.burlock.org/ubuntu/196-disabling-the-mouse-scroll-wheel-left-and-right-click-for-ubuntu-1010](http://blog.burlock.org/ubuntu/196-disabling-the-mouse-scroll-wheel-left-and-right-click-for-ubuntu-1010)

but this hasn't stopped it, not sure why.

---

### Post by bikegeek on 2010-11-21
This has been pissing me off for months, however, there's a fix here:

[https://bugs.launchpad.net/ubuntu/+bug/636720](https://bugs.launchpad.net/ubuntu/+bug/636720)

Run:

> synclient ClickFinger3=1

To make permanent:
cat /usr/share/X11/xorg.conf.d/50-synaptics.conf
> Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        # Stop the middleclick insanity
        Option "ClickFinger3" "1"
EndSection


So, to me, it appears that sometimes the touchpad thinks you've got 3 fingers down while clicking the left button... by default, this is configured to emulate a middle click. The above changes that behavior to emulate a left-click.

---

### Post by kurtpete on 2011-01-01
Oh my, thank you, thank you, thank you!  This has been driving me nuts for months (luckily just on a occasionally used laptop).  It appears to have been my issue, and this resolved it.  Again, thank you!

> **bikegeek said:**
> This has been pissing me off for months, however, there's a fix here:

[https://bugs.launchpad.net/ubuntu/+bug/636720](https://bugs.launchpad.net/ubuntu/+bug/636720)

Run:



To make permanent:
cat /usr/share/X11/xorg.conf.d/50-synaptics.conf



So, to me, it appears that sometimes the touchpad thinks you've got 3 fingers down while clicking the left button... by default, this is configured to emulate a middle click. The above changes that behavior to emulate a left-click.

---

### Post by waltherg on 2011-02-02
I'm sorry, I am an absolute beginner. How do I edit the .conf file to add in that line? This issue has been driving me crazy for too long.

Thanks in advance,

Greg

---

### Post by gsgleason on 2011-02-21
My my god, thank you!  I have been going crazy!

I hope this does it.


waltherg:

You can do this by pressing Alt+f2, then in the run application box, type "gksu gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf"

---

