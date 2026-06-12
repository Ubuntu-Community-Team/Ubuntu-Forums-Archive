---
title: "Kanvus Note A4"
date: 2012-11-11
forum: Hardware
---

### Post by fillemazendacus on 2012-11-11
Hello!

I'm newbie in Ubuntu Studio (12.10) with tablet.
Kanvus Note A4 does not want to contact (it worked with Windows 7)..
It seems every tutorial talking about Wacom or is it something universal? Anyway none of them didn't helped me..
Is it impossible to get it to work here? :confused:

---

### Post by Favux on 2012-11-11
Hi fillemazendacus,

Welcome to Ubuntu forums!


Since these sort of tablets are often re-branded lets find out who made your tablet and what model it is.  What is the output of the the following command in a terminal?
```
lsusb
```

---

### Post by fillemazendacus on 2012-11-11
Hey! Thanx for react! :)

So, it says:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 053: ID 5543:6003 UC-Logic Technology Corp. 
Bus 003 Device 010: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 002: ID 2109:0811  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c31d Logitech, Inc. 
Bus 001 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 050: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
```

and Device 053 seems to be actual line:
```
Bus 003 Device 053: ID 5543:6003 UC-Logic Technology Corp.
```

---

### Post by Favux on 2012-11-11
Alright.

The **Kanvus Note A4** appears to be a new model (6003) UC-Logic tablet (5543).  It does not have a "fixed" kernel driver that will work with the evdev X driver according to DIGI*mend*:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

It doesn't appear the diagnostics for the tablet have been submitted to the DIGI*mend* project yet.  In which case they should be:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Collecting_tablet_diagnostics)

In the meantime we could try setting it up on evdev anyway but probably the best bet is to use the WizardPen driver:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)

Using WizardPen hasn't been tested in Quantal (12.10) yet but we know it does compile.

---

### Post by fillemazendacus on 2012-11-11
Well, I stopped in line

> **Custom tablet .conf**

Everything installed fine, but so far tablet don't works..
It seems I must do that *custom .conf file*-stuff, but I have no idea, how.. Can you help me in this? I must write some text-file myself?

---

### Post by Favux on 2012-11-11
Sure.  What is the output of this command in a terminal?
```
xinput list
```
Do you have a xorg.conf.d directory in /etc/X11, i.e. /etc/X11/xorg.conf.d?

---

### Post by fillemazendacus on 2012-11-11
```
   &#8627; UC-LOGIC DIGITAL-Organizer              	id=11	[slave  pointer  (2)]

```

Oh sorry, I didn't saw next question.
No, here is not any xorg directory in X11..

---

### Post by fillemazendacus on 2012-11-11
Ahaa..

I have now open 52.tablet.conf and i must write something like that?

```
Section "InputClass"
        Identifier "UC-Logic DIGITAL-Organizer"
        MatchIsTablet "on"
        MatchProduct "UC-Logic"
        MatchDevicePath "/dev/input/event*"
        Driver "wizardpen"
        # Apply custom Options below.
EndSection
```

---

### Post by Favux on 2012-11-11
Yes.  But use **UC-LOGIC**.

And that was the only tablet line in the output of **xinput list**?

---

### Post by fillemazendacus on 2012-11-11
UPS, I tought so.. full xinput was this:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC DIGITAL-Organizer              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                   	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                   	id=9	[slave  keyboard (3)]

```

---

### Post by Favux on 2012-11-11
Thanks.

So you could combine the two UC-Logic models we now know about with this .conf file:
```
Section "InputClass"
        Identifier "UC-Logic tablet"
        MatchIsTablet "on"
        MatchProduct "UC-LOGIC|H850S"
        MatchDevicePath "/dev/input/event*"
        Driver "wizardpen"
        # Apply custom Options below.
EndSection
```
Assuming the MatchIsTablet line works for you too.

---

### Post by fillemazendacus on 2012-11-11
Right now is result that I can make in Gimp points, but pen does not move..

Edit: I try it! (I didn't saw next page.. :D )
But still the same - even buttons on pen are working, but pen does not move..

---

### Post by Favux on 2012-11-11
Well shoot.  How about something else like MyPaint?

Assuming the match is successful and the tablet is on the WizardPen driver that may indicate your tablet does not work on the WizardPen driver.

Could you post the output of **Xorg -version** in a terminal?

Could you compress your Xorg.0.log (right click on it and choose Compress) in /var/log and attach it to your next post?  That might tell us what is happening.

---

### Post by fillemazendacus on 2012-11-11
> X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
Current Operating System: Linux Mazendacum 3.5.0-18-lowlatency #18-Ubuntu SMP PREEMPT Fri Oct 19 22:17:40 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-lowlatency root=UUID=e77e7715-81de-4aff-8491-abba2318c819 ro quiet splash vt.handoff=7
Build Date: 08 October 2012  03:34:01PM
xorg-server 2:1.13.0-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.26.0
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.


Pen does not move at all, in whole Ubuntu, but when it stays in "right" place, it can open menus or makes selections and so on.. :(

---

### Post by Favux on 2012-11-11
Oops.  Need the Xorg.0.log not Xorg.0.log.old.  Tablet and WizardPen aren't in that one.  And you're restarting, correct?

Where is the pointer stuck?  It sounds like the WizardPen driver isn't sending X and Y coordinates to the X Server.  I'm hoping the WizardPen driver might just need tablet's coordinates.

---

### Post by fillemazendacus on 2012-11-11
[COLOR="Green"]Oh-Me-Stuped[/COLOR]

So, after restart we have some progress:
Now pointer stuck is left-top of display, working very slowly and in very little area, something like 10x10cm.. :D

---

### Post by Favux on 2012-11-11
Progress!  :)

Your Xorg.0.log now shows the tablet setting up on WizardPen:
> [   232.169] (II) config/udev: Adding input device UC-LOGIC DIGITAL-Organizer (/dev/input/event16)
[   232.169] (**) UC-LOGIC DIGITAL-Organizer: Applying InputClass "evdev tablet catchall"
[   232.169] (**) UC-LOGIC DIGITAL-Organizer: Applying InputClass "UC-Logic tablet"
[   232.169] (II) LoadModule: "wizardpen"
[   232.169] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[   232.196] (II) Module wizardpen: vendor="X.Org Foundation"
[   232.196] 	compiled for 1.13.0, module version = 0.8.1
[   232.196] 	Module class: X.Org XInput Driver
[   232.196] 	ABI class: X.Org XInput driver, version 18.0
[   232.196] (II) Using input driver 'wizardpen' for 'UC-LOGIC DIGITAL-Organizer'
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: always reports core events
[   232.196] (**) Option "Device" "/dev/input/event16"
[   232.196] (--) UC-LOGIC DIGITAL-Organizer: MaxX:21600 MaxY:16800 MaxZ:511
[   232.196] (--) UC-LOGIC DIGITAL-Organizer: aspect ratio:1.00:1
[   232.196] (**) UC-LOGIC DIGITAL-Organizer is in absolute mode
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: TopX not set, defaulting to "5%"
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: TopY not set, defaulting to "5%"
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: BottomX not set, defaulting to "95%"
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: BottomY not set, defaulting to "95%"
[   232.196] (II) UC-LOGIC DIGITAL-Organizer: ScreenX = 1920, ScreenY = 1080
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: TopX                   = 1080
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: TopY                   = 840
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: BottomX                = 20520
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: BottomY                = 15960
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: TopZ    (min pressure) = 0
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: BottomZ (max pressure) = 511
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: always reports core events
[   232.196] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input16/event16"
[   232.196] (II) XINPUT: Adding extended input device "UC-LOGIC DIGITAL-Organizer" (type: WizardPen Tablet, id 11)
[   232.196] (II) UC-LOGIC DIGITAL-Organizer Increment: 11
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: (accel) keeping acceleration scheme 1
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: (accel) acceleration profile 0
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: (accel) acceleration factor: 2.000
[   232.196] (**) UC-LOGIC DIGITAL-Organizer: (accel) acceleration threshold: 4
[   232.196] (II) config/udev: Adding input device UC-LOGIC DIGITAL-Organizer (/dev/input/mouse1)
[   232.197] (II) No input driver specified, ignoring this device.
[   232.197] (II) This device may have been added with another device file.
And it looks good.  Furthermore:
> Now pointer stuck is left-top of display, working very slowly and in very little area, something like 10x10cm.
suggests, with luck, that WizardPen does just need the tablet coordinates to work.

If it was stuck in the top left corner (the origin or 0,0) it would mean WizardPen isn't sending coordinates to the X Server.  So now we need to figure out the tablet coordinates.  Normally you use a calibration program like xinput_calibrator (Calibrate Touchscreen in Software Center).  But if you can't get to the bottom right corner that probably won't help much.

So we need to know the resolution or LPI (lines per inch) of the tablet.  And the tablet's **active area** in inches.  Or cm's if that's what the specifications for the tablet use.  Do you have that on the box or manual?  Or know a web site that has that information?

---

### Post by fillemazendacus on 2012-11-11
In [this page]("http://www.kanvus-global.com/main/prod_in.aspx?mnuid=1524&modid=26&prodid=335&flag=1") under Specification it says:

```
Writing Area	A4 size&#65306;210 x 297mm
                Letter size &#65306;215.9 x 279.4 mm


Resolution            2000 LPI
Report Rate           200RPS
Pressure Sensitivity  1024 Level
```

(And actually before pen stucked everywhere, where I moved it with mouse..)


Edit: oh, letter is probably only normal paper in complect..

---

### Post by Favux on 2012-11-11
Hmm.  So it isn't actually a tablet.  There's a sensor tracking the pen in the upper left corner?  And a pad of paper?  Regular paper?  Are you using it without the paper?  Do you turn it sideways?

Hmmm.  Then the Y is longer than X.  Usually on a tablet X is longer than Y like on a monitor.  So that aspect ratio mismatch would be some of the problem.  Why it doesn't cover the whole monitor.

Writing Area:
A4 size&#65306;210 x 297mm
Letter size &#65306;215.9 x 279.4 mm

Use largest dimension on both axis since it the sensor handles it?
21.59 x 29.7 cm

8.50 x 11.69 inch


2000 LPI (and using 2.54 cm/inch):
Bottom X = 8.50 x 2000 = 17,000

Bottom Y = 11.69 x 2000 = 23,380

So?
```
Section "InputClass"
        Identifier "UC-Logic tablet"
        MatchIsTablet "on"
        MatchProduct "UC-LOGIC|H850S"
        MatchDevicePath "/dev/input/event*"
        Driver "wizardpen"
        # Apply custom Options below.
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"17000"
	Option		"BottomY"	"23380"
EndSection
```

---

### Post by fillemazendacus on 2012-11-12
Thank you so much for help!
I feel myself like human again! :D

Those numbers was just a headache to find right ones (hundreds of restarts), but finally works for me this set (for taking whole display, tablet going out of this because of mismatched dimensions):
```
	Option		"TopX"		"-10"
	Option		"TopY"		"45"
	Option		"BottomX"	"4020"
	Option		"BottomY"	"2842"
```

And yes, it IS tablet.. :D  Sorry for misguide you.. In this completion are 2 pens in same time ink-pens too - you have paper to see on tablet what you are drawing/writing.. :)

So, thank you again, Favux, you are very helpful! :)

---

### Post by Favux on 2012-11-12
Very nice job!!  :)

Thank you for explaining the paper pad on the tablet.  There for notes but not needed.

So you can't use the bottom part of the tablet?  Like this?
```
---------
|       |
|       |
|       |
|xxxxxxx|
|xxxxxxx|
---------
```

---

### Post by fillemazendacus on 2012-11-12
Actually something like this, because display's X is longer than A4 (and this is landscape too):

```

--------------
|            |
|            |
|            |
|xxxxxxxxxxxx|
|xxxxxxxxxxxx|
--------------

```

But it's ok - I can zoom on screen in and out without loosing quality.. :) I already fell to draw like in dreams.. :D

---

