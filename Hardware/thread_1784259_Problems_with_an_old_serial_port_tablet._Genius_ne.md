---
title: "Problems with an old serial port tablet. Genius newsketch 1212HR."
date: 2011-06-16
forum: Hardware
---

### Post by Pablo33 on 2011-06-16
Hi, I'm just wondering if I will finally get working an old tablet.
It's the Genius Newsketch 1212HR, and it is attached to a serial port.

I've read in the forum old threads about that and I've tried to configure it via /etc/X11/xorg.conf


After creating a first xorg configuration, i added the lines related to "SummaSketch II+"
and I've also noticed that "summa" module is not loaded on the kernel. Is there another new module for tablets? (serial attached tablets)
Here's my /etc/X11/xorg.conf
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "SummaSketch II+" "SendCoreEvents"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dbe"
    Load  "glx"
    Load  "summa"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
    Identifier  "SummaSketch II+"
    Driver      "summa"
    Option      "Device" "/dev/ttyS0"
    Option        "InputFashion" "Tablet"
    Option      "Cursor" "Stylus"
    Option      "SendCoreEvents" "on"
    Option      "Compatible" "True"
    Option      "Protocol" "Auto"
    Option      "Mode" "Absolute"
    Option      "Name" "SUMMASKETCH"
    Option      "Vendor" "SUMMAGRAPHICS"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```and here's my /var/log/Xorg.0.log
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux pablo-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=c422d80c-f6a9-4a76-90ef-1c3703a6d27a ro quiet splash
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 16 23:58:10 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Parse error on line 46 of section InputDevice in file /etc/X11/xorg.conf
    "Identifier"SummaSketch" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```I'm running ubuntu 10.04.

Any comment or help will be appreciated. The tablet is very old in age, but it looks as it were new.

---

### Post by Favux on 2011-06-16
Hi Pabl033,

I'm sorry but I don't think you can find a currently working serial X driver for it on Lucid's 1.7 Xserver.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1262421](http://ubuntuforums.org/showthread.php?t=1262421)

I doubt that it really is that big a deal to get it working again.  Some ABI changes for the newer Xserver are probably all that's needed.  Something an Xorg dev. could probably do fairly easily.

You might get lucky if you try to compile the source code.  Sometimes when you google the error message(s) you can find simple fixes you can apply to the source code yourself.

---

### Post by Pablo33 on 2011-06-17
Hi Favux, thanks for your comment. It has been very explanatory.

> **Favux said:**
> Hi Pabl033,
You might get lucky if you try to compile the source code.  Sometimes when you google the error message(s) you can find simple fixes you can apply to the source code yourself.

Could be, I'll try google, but I think I have an old museum piece. :P
Thanks again.

---

### Post by Favux on 2011-06-25
Hi Pablo33,

I was thinking if you haven't gotten anywhere on your googling you could maybe have a look at inputattach.  It's in the repositories.  No mention about your device having support, but maybe you'd get lucky and one of the touchscreens or supported mouses has a protocol similar enough to your SummaSketch for it to "work".

---

### Post by Pablo33 on 2011-06-26
Ok, good idea, 

**testing inputattach**

```
sudo inputattach --always -t213 /dev/ttyS0
```    (Shara Touch-iT213 Tablet PC) >> nothig happend  (and gives error initializing tablet)
    
```
sudo inputattach --always -vs /dev/ttyS0
```    DEC VSXXX-AA / VSXXX-GA mouse and VSXXX-A tablet) >> anulates my synaptics laptop's buttons and sometimes appears the contextual menu on screen while moving or clicking the stylus on the tablet.

```
sudo inputattach --always -vs /dev/ttyS0
sudo inputattach --always -tw /dev/ttyS0
```    (Touchwindow serial touchscreen) >> hangs up the computer.

```
sudo inputattach --always -elo3b /dev/ttyS0    
```    nothing happens, ( and even elo4, elo6, elo....)

The tablet has two options to emulate microsoft mouse and "mouse system mouse".  Let's try them!

```
sudo inputattach --always -bare /dev/ttyS0
```    (2 button microsoft pointer)
    mouse pointer turns to a funny frenetic and of course uncontrollable shaking way. Seems suffers from parkinson moving around a 25 pixels area. X-DD     the best, is that buttons 1 and 2 works properly.  after all, It seems that more or less  I can control directional movements.

```
sudo inputattach -ms3 /dev/ttyS0
```    (Microsoft intellimouse) >> the same shaking symptoms 
```
sudo inputattach -msc /dev/ttyS0
```    (Microsoft intellimouse) >> the same shaking symptoms 


```
sudo inputattach -mtouch /dev/ttyS0
```    (Microsoft 3M touchscreen)  Well, pointer only moves and/or is shown when a button is pressed. It works as it were a tablet, but the whole tablet area corresponds to a quarter of my laptop screen. It suffers from parkinson again,but less.

```
sudo inputattach -pm /dev/ttyS0
```    (penmount touchscreen) > turns uncontrollable, and pointer disappears


Well, finally  I think that mouse emulation works, but it isn't fine at all. 

On the other hand, the option -mtouch (Microsoft 3M touchscreens), works like a tablet does, although I must press one button to see the cursor, but there are a direct and absolute concordance between a point at the tablet and a point on the screen. But there is still shaking symptoms, buttons doesn't work as mouse or pointer buttons, and I can't set up a valid concordance between areas (whole tablet and whole screen).

Thanks again, it was a very good idea :)   but I think I should forget about this tablet.

---

### Post by Favux on 2011-06-26
Hi Pablo,

Nice work!

We may be able to get somewhere with the Microsoft 3M touchscreen protocol:
> (Microsoft 3M touchscreen) Well, pointer only moves and/or is shown when a button is pressed. It works as it were a tablet, but the whole tablet area corresponds to a quarter of my laptop screen. It suffers from parkinson again,but less.

On the other hand, the option -mtouch (Microsoft 3M touchscreens), works like a tablet does, although I must press one button to see the cursor, but there are a direct and absolute concordance between a point at the tablet and a point on the screen. But there is still shaking symptoms, buttons doesn't work as mouse or pointer buttons, and I can't set up a valid concordance between areas (whole tablet and whole screen).

If the tablet is represented by a quarter of the screen we might be able to fix the coordinates, say using xinput.  That might even help with the shaking.  Don't quite know what to do with the pointer only showing on a button press and the buttons not working.  But since:
> X-DD the best, is that buttons 1 and 2 works properly.
To be honest it sounds like with some coding someone could come up with a SummaSketch driver by mushing the X-DD and Microsoft 3M code together.

While running each protocol enter *xinput list* in a terminal and post the output.  What we want to do is get the "device name" for the tablet so we can enter in a terminal for each protocol:
```
xinput list-props "device name"
```
And see if the list-props output gives us enough clues for things to modify with *xinput set-prop* (see *man xinput*).

---

### Post by Favux on 2011-06-26
Hmm.  I can't find an inputattach home site on sourceforge or whatever.  Can you?  But the source code is out there.  I got it from the linuxwacom site in the [input-wacom package]("http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/").  I figured we could check out how they added the wacom tablet and what is involved.

Sure enough it may be doable if you got real lucky.  Barring a coder, who knows what they're doing, dropping in.  Looking at the wacom addditions and starting with mtouch, since that kind of works:
```
{ "--mtouch",		"-mtouch",	"MicroTouch (3M) touchscreen",
	B9600, CS8 | CRTSCTS,
	SERIO_MICROTOUCH,	0x00,	0x00,	0,	NULL },
```
So I think we can safely guess the SummaSketch is 9600 baud.  Does that sound right?  A question for later is do you need the CRTSCTS?  But let's leave that alone.
```

{ "--summasketch",	"-summasketch",	"SummaSketch II+",
	B9600, CS8 | CRTSCTS,
	SERIO_MICROTOUCH,	0x00,	0x00,	0,	NULL },

```
Obviously a shot in the dark but if that actually worked then what would:
```
{ "--summasketch",	"-summasketch",	"SummaSketch II+",
	B9600, CS8 | CRTSCTS,
	SERIO_MICROTOUCH,	0x00,	0x00,	1,	NULL },
```
do?  Clearly I only have the vaguest idea of where some of the values are coming from.  And I don't understand what you did with:
> X-DD the best, is that buttons 1 and 2 works properly. 
It might help if you explained that and showed the command you used.

But if you wanted to tinker you might come up with something.  Obviously after we figured out the coordinates and what not as in the above post.

---

### Post by Pablo33 on 2011-06-27
Ok, let's see. Firstly, I want to clear a misunderstanding, "X-DD" is not a protocol or something similar, it was a smiley laughing . I'm really sorry about that.

The tablet has two modes of mouse emulation, therefore, it must work as it were a real serial mouse. Well, the pity is that in that mode the pointer also suffers from shaking, so I start thinking that the tablet must be slightly broken. It was in that emulation mode when the buttons worked properly, as it was working as a serial mouse.

I've tested it within win XP, and has the same symptoms. So linux and his inputattach module aren't the problem.


Your suggestion:

```
~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9116;   &#8627; **MicroTouch Serial TouchScreen               id=12    [slave  pointer  (2)]**
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

``````
~$ xinput --list-props** 12**
Device 'MicroTouch Serial TouchScreen':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axis Calibration (317):    <no items>
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Abs X" (543), "Abs Y" (544)
    Button Labels (320):    "Button Unknown" (315), "Button Unknown" (315), "Button Unknown" (315), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```Meanwhile inputattach with  -mtouch protocol is running I can't get buttons work.

Since the tablet doesn't work properly running in mouse emulation mode, I'm convinced there's something wrong with hardware. It should work fine!, and I remember it worked fine years ago.

what do you think at this respect?, thanks for all your effort.

---

### Post by Favux on 2011-06-27
> I've tested it within win XP, and has the same symptoms. So linux and his inputattach module aren't the problem.
So it could be a hardware problem.  With a Wacom tablet I'd check for a source of electromagnetic interference too close to the tablet.  Since your tablet doesn't work that way I'd make sure the serial connection was firm and clean.  Not being a Wacom your stylus probably uses a battery.  Is it new or old?  I'd also try to turn off or unplug other things running on the Desktop and see if interference is coming from them.  If it is a capacitor or something failing on the tablet you'd have to spot it, failed capacitors are often pretty obvious, and replace it.  If you can disassemble the tablet and your soldering skills are up to it.

For the screen coverage from *man evdev*:
> Option "Calibration" "min-x max-x min-y max-y"
    Calibrates the X and Y axes for devices that need to scale to a different coordinate system than reported to the X server. This feature is required for devices that need to scale to a different coordinate system than originally reported by the kernel (e.g. touchscreens). The scaling to the custom coordinate system is done in-driver and the X server is unaware of the transformation. Property: "Evdev Axis Calibration".

Evdev Axis Calibration
    4 32-bit values, order min-x, max-x, min-y, max-y or 0 values to disable in-driver axis calibration. 

To set the calibration the runtime command you enter in a terminal I think would be in the form of (from *man xinput*):
```
xinput set-prop "device name" "property name" value
```
Do you have the coordinates from an old xorg.conf or something?  Otherwise you may have to guess.  I don't know if xinput_calibrator would work for you.  So something like:
```
xinput set-prop "MicroTouch Serial TouchScreen" "Evdev Axis Calibration" 0 10000 0 6000
```
Using your coordinates of course
> The tablet has two modes of mouse emulation, therefore, it must work as it were a real serial mouse.
Right I am interested in the exact command you used so I can see if we should set a different long integer for type emulation in the code.

If we get the coordinates settled we can then move onto the buttons.  Because there are unknown buttons:
> Button Labels (320):    "Button Unknown" (315), "Button Unknown" (315), "Button Unknown" (315), "Button Wheel Up" (156), "Button Wheel Down" (157)

I'm thinking there is something you could do there.  If we figure out how to set buttons for evdev.

---

### Post by Pablo33 on 2011-06-28
Hello, good news!:guitar:

Hardware problem detected and solved. It was the power supply. I feel a bit guilty about that. I really didn't know where was the original tablet's power supply, or if it were broken, I just can't remember; so I connected another one (a multi voltage supply - 500ma) set +5V DC and plug it,  As a result it sent lots of noise and interference to the tablet which came up with the terrible shaking symptoms. I decided to take the power from another device, the computer's unit should be enough.
After the test, the tablet worked as it were its first day!!!     fine and smooth. :P

I've tested again mouse emulation modes and both of them works perfectly. Here goes some code result. Mouse mode doesn't have any mystery, except using more than 2 buttons. But I don't mind it, it's just a two button serial mouse.


(  -bare (2-button Microsoft mouse-emulation)
```
~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button  emulation            id=11    [slave  pointer  (2)]
** &#9116;   &#8627; Microsoft Mouse                             id=12    [slave  pointer  (2)]**
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
```

( -msc  (**mouse systems mouse-emulation**) - *Stylus plugged*)
```
~$ xinput --list-props 12
Device '**Mouse Systems Mouse**':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Rel X" (160), "Rel Y" (161)
    Button Labels (320):    "Button Left" (153), "Button Middle" (154), "Button Right" (155), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```

( -msc  (**mouse systems mouse-emulation**) - puk plugged)
```
~$ xinput --list-props 12
Device '**Mouse Systems Mouse**':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Rel X" (160), "Rel Y" (161)
    Button Labels (320):    "Button Left" (153), "Button Middle" (154), "Button Right" (155), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```

******************************************************
ok, now 2-button mouse protocol

( option -bare  (**2-button Microsoft mouse-emulation**) - *Stylus plugged*)
```
~$ xinput --list-props 12
Device '**Microsoft Mouse**':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Rel X" (160), "Rel Y" (161)
    Button Labels (320):    "Button Left" (153), "Button Unknown" (315), "Button Right" (155), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```

( -bare  (**2-button Microsoft mouse-emulation**) - *puk plugged*)
~$ xinput --list-props 12
```
Device '**Microsoft Mouse**':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Rel X" (160), "Rel Y" (161)
    Button Labels (320):    "Button Left" (153), "Button Unknown" (315), "Button Right" (155), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```


I'll repeat -mtouch output code. with the puk conected.
```
~$ xinput --list-props 12
Device 'MicroTouch Serial TouchScreen':
    Device Enabled (152):    1
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (273):    1.000000
    Device Accel Velocity Scaling (274):    10.000000
    Evdev Reopen Attempts (269):    10
    Evdev Axis Inversion (316):    0, 0
    Evdev Axis Calibration (317):    <no items>
    Evdev Axes Swap (318):    0
    Axis Labels (319):    "Abs X" (543), "Abs Y" (544)
    Button Labels (320):    "Button Unknown" (315), "Button Unknown" (315), "Button Unknown" (315), "Button Wheel Up" (156), "Button Wheel Down" (157)
    Evdev Middle Button Emulation (321):    2
    Evdev Middle Button Timeout (322):    50
    Evdev Wheel Emulation (323):    0
    Evdev Wheel Emulation Axes (324):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (325):    10
    Evdev Wheel Emulation Timeout (326):    200
    Evdev Wheel Emulation Button (327):    4
    Evdev Drag Lock Buttons (328):    0

```


Some points:

Sometimes, not very often, while the tablet is working though touch-screen protocol, seems that inputattach crashes or something else, and I have to kill inputattach process and restart it again. But I think this behaviour could be rather normal, as the tablet has a reset button that I have to push sometimes to restart his own protocol (even in mouse-emulation mode, but in this case inputattach doesn't crash).

While -mtouch protocol is running, I can control my laptop touchpad and their buttons in X without problems. I mean, that I can use at the same time the tablet and use synaptic touch-pad buttons (or another mouse button) to draw,select or anything else.

The tablet is very old, the stylus and puk are wire-connected.


So inputattach works, mouse-modes works, tablet could work as a tablet.   I feel happy!.

Next try: configure the X device "MicroTouch Serial TouchScreen" to extend the operating area to the whole screen. I do not have any old xorg.conf or something else. So I'll guess coordinates and values. It seems easy. Other thing is configure buttons. I still feel as a linux newbie since ubuntu 10.04 release was my first linux touch.

Thanks again for your persistence.

---

### Post by Favux on 2011-06-28
Really nice work diagnosing a noisy power supply!

Thank you for hanging in there.  We've now got a old serial SummaSketch "working"!  Real progress.

I hope calibration isn't too tough.  I'm eager to see the results.  Again you could try xinput_calibrator:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)  I'm just not sure how helpful it will be.

---

### Post by Pablo33 on 2011-06-29
Testing Tablet

Hello, another step successfully reached.

Downloaded xinput_calibrator package, and installed.
read the manual   ~$ man xinput_calibrator
and run it. It has been some tricky.

The program shows a white screen with four crosses , step by step I have to click them in order of showing. I have to "touch" the "touch screen", but instead, I have to click each cross with the stylus, and then do click with mouse button. It doesn't mind if the pointer doesn't "really points" over the cross on the screen, just click more or less the same area on the tablet, and then click mouse. It's in this moment when a point is calibrated, taking xinput_calibrate the coordinate from the last received coordinate. 

Once the four crosses are clicked, the tablet is calibrated enough to be plenty useful.

But, since my screen is a wide-screen and tablet's area is 12" square, If I want to match both axes to same dpi response at movement, the only thing I have to do is to make a mask (template) with the four crosses and plot it on a paper. Although you have to "click"  each cross, the puk must click this time just over each cross marked ant the tablet.

I took four screen-shots while a calibration and Gimp helped me to make the rest. paper mask must be 12" wide, same as  the tablet, in case we want to make the most of space. But don't matter if it's a bit little, because we always can calibrate.... and re-calibrate.:)

Ok, so, I can calibrate the tablet as it were a touch screen, I can move and see the cursor (while a button is pressed). It's more than I expected. :P

Yes, it has been very useful your help! 

Any idea about make buttons working?, or show the cursor always, and not only when a button is pressed?.

PD: some output code from calibration.
```
~$ sudo xinput_calibrator 
Calibrating EVDEV driver for "MicroTouch Serial TouchScreen" id=11
    current calibration values (from XInput): min_x=75, max_x=5892 and min_y=12369, max_y=16009

Doing dynamic recalibration:
    Setting new calibration data: 201, 5997, 11992, 15008


--> Making the calibration permanent <--
  Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
    xinput set-int-prop "MicroTouch Serial TouchScreen" "Evdev Axis Calibration" 32 201 5997 11992 15008

```

---

### Post by Pablo33 on 2011-07-01
Well, here I go again.

This could be considered as a possible hardware workaround.
[IMG]http://img825.imageshack.us/img825/6531/1007374.jpg[/IMG]

This is my wireless optical mouse over the puck. Button "one" on the puck must be permanently pressed. The movement is registered by the puck and sent to X11 within inputattach -mtouch option. Mouse buttons are fully operative. Then you have to calibrate with xinput_calibrator tool.  

There's one bug, the puck has to be permanently in touch with the tablet, otherwise protocol will fail and you'll have to start the process again by loading inputattach and calibrating.

It's crazy, but it works. I think this thread could be mark as solved, since tablet is working again, and there is no notice about to make it work with his own summa module.

I still think that it should be very easy to add a protocol for this tablet in inputattach, but I don't know how, I'm only an user. :)

Thanks again!, Favux. :popcorn:

---

### Post by Favux on 2011-07-01
Hi Pablo33,

Awesome!

I haven't forgotten you.  I was busy with my Wacom Serial tablet HOW TO project.

The paper mask to make a calibration template was ingenious.

So to sum it up you install inputattach from the repositories using Synaptic Package Manager.  Then to get your tablet events reporting on /dev/input you run the command:
```
sudo inputattach -mtouch /dev/ttyS0
```
Then the SummaSketch shows up in xinput list as:
> "MicroTouch Serial TouchScreen"
Using xinput_calibrator and the template (to map your tablet to your widescreen monitor) you got the coordinates:
> Doing dynamic recalibration:
    Setting new calibration data: 201, 5997, 11992, 15008

And the command to implement them is:
```
xinput set-int-prop "MicroTouch Serial TouchScreen" "Evdev Axis Calibration" 32 201 5997 11992 15008
```
Then you set up the two commands in a start up script.  And as long as you have the puck in touch with tablet at all times it works.



The lashup with your mouse over the puck with the optical crosshairs to get working mouse buttons is also clever.  By the way does the SummaSketch come with a stylus too, or just the puck?

> I still think that it should be very easy to add a protocol for this tablet in inputattach, but I don't know how, I'm only an user. 
I don't know if I could either.  But if I had a SummaSketch to test with I would probably try and see if I could hack something up in the code.

But if we were very lucky we might not need to.  That is what I was talking about in post #7.  If we added something like:
```
{ "--summasketch",	"-summasketch",	"SummaSketch II+",
	B9600, CS8 | CRTSCTS,
	SERIO_MICROTOUCH,	0x00,	0x00,	1,	NULL },
```
to the inputattach source code file inputattach.c, or maybe substituted it in for the microtouch code could we get it working better?  This is in the  static struct input_types input_types section.  We'd could try playing with that anyway if we can figure out how to compile inputattach which probably isn't too hard and the input-wacom stuff might help with that.  This would avoid trying to trace through the actual code and changing it.

Like I say we'd have to get lucky.  For example I don't know if we could fix the always in proximity thing without actually changing the code.

We still haven't looked at using xinput on the buttons.  What is your current *xinput list* and *xinput list-props* with your working setup?  Even if standard button mapping commands don't work there must be some documentation about working with buttons on the evdev driver.  How many buttons does the puck have and where are they and what are they suppose to do?

---

### Post by Pablo33 on 2011-07-01
> **Favux said:**
> Hi Pablo33,
Awesome!
I haven't forgotten you.  I was busy with my Wacom Serial tablet HOW TO project.

:) don't worry, I'm not in a hurry. :)


> **Favux said:**
> 
So to sum it up .....
....install inputattach 
sudo inputattach -mtouch /dev/ttyS0....
xinput_calibrator and the template-....
And the command to implement them is:.....
Then you set up the two commands in a start up script.
I haven't already done the last part because it's very easy set up and calibrate the tablet. But someday I will.
> **Favux said:**
>  And as long as you have the puck in touch with tablet at all times it works.
Yes. 
> **Favux said:**
> The lashup with your mouse over the puck with the optical crosshairs to get working mouse buttons is also clever.  By the way does the SummaSketch come with a stylus too, or just the puck?
Both of them, I can use stylus too, by blinding the mouse and using it with my left hand to click buttons meanwhile I press the stylus to see the cursor. The related bug disappears if the stylus button is not pressed.  Yes, I think that operate with the puck is better. O:)


> **Favux said:**
> ....We still haven't looked at using xinput on the buttons.  What is your current *xinput list* and *xinput list-props* with your working setup?  Even if standard button mapping commands don't work there must be some documentation about working with buttons on the evdev driver.  How many buttons does the puck have and where are they and what are they suppose to do?

Ok, ok, let's give a try.

I downloaded source code of inputattach (or I think so). 
FILE: "inputattach_1.23.orig.tar.gz"
contains: 
inputattach.c
inputattach.1

File: joystick_20051019.orig.tar.gz
also contains inputattach.c among other files.

I think I know where to insert your code (there are similar lines), but I don't know how to compile after this.

my installed version of inputattach : "20051019-9" 

```

**~$ xinput list-props 11**
    Device 'MicroTouch Serial TouchScreen':
    Device Enabled (121):    1
    Device Accel Profile (245):    0
    Device Accel Constant Deceleration (246):    1.000000
    Device Accel Adaptive Deceleration (248):    1.000000
    Device Accel Velocity Scaling (249):    10.000000
    Evdev Reopen Attempts (238):    10
    Evdev Axis Inversion (250):    0, 0
    Evdev Axis Calibration (251):    187, 6012, 11427, 15103
    Evdev Axes Swap (252):    0
    Axis Labels (253):    "Abs X" (243), "Abs Y" (244)
    Button Labels (254):    "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239), "Button Wheel Up" (125), "Button Wheel Down" (126)
    Evdev Middle Button Emulation (255):    2
    Evdev Middle Button Timeout (256):    50
    Evdev Wheel Emulation (257):    0
    Evdev Wheel Emulation Axes (258):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (259):    10
    Evdev Wheel Emulation Timeout (260):    200
    Evdev Wheel Emulation Button (261):    4
    Evdev Drag Lock Buttons (262):    0

``````
~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. Wireless Keyboard & Mouse      id=9    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9116;   &#8627; MicroTouch Serial TouchScreen               id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; MOSART Semi. Wireless Keyboard & Mouse      id=8    [slave  keyboard (3)]

```Stylus has two buttons, normally corresponds with "the two main buttons" of a mouse.
puck has four buttons, and I don't know what they are supposed to do. (except first and second, that are the same buttons as stylus)

well, don't worry, take your time with this thread, now it's my turn to thank you for hang in there. :)  I knew you haven't forgotten me, but I supposed there weren't much more to do. What's next step? try to change and compiling inputattach? 

PD: I've been using this invention with the puck for about 2 hours without any errors, and still using it. inputattach works!, linux works!, love linux :KS

---

### Post by Favux on 2011-07-05
Hi Pablo33,

Maintenance for inputattach was dropped.  But guess what?  It got picked up again in April of this year as part of Linux Console tools:  [http://sourceforge.net/projects/linuxconsole/](http://sourceforge.net/projects/linuxconsole/)

So now you have a place to get the official source code, put in a support request and ask for a feature request, like support for the SummaSketch.  I don't know how active the site is but I know a linux wacom developer is planning to submit both the pen and touch and pen only code.

---

### Post by Pablo33 on 2011-07-06
Marvelous Favux,  a little light again. I performed your advice.

It's being grateful using this tablet with the stylus, even in mouse emulation, Inkscape just runs as never has done. How could I thank you?.:popcorn:

I hope SummaSketch code would be considered again and put.

by the way, just a question, how could I change/configure stylus dpi response (I mean within his mice emulations) without also changing the response of other mouse devices attached (I mean the other usb mouse for example). I want to accurate my stylus aim.

Is it using **xinput** command?   thanks again for your involvement.

---

### Post by diggy128 on 2011-08-29
Hi.
Resurrecting the thread.
I have a very old (1997) Wintime penpal MT-604 A5 tablet (with mouse and stylus). Was working fine under XP, with Vista BSOD so no game.

Having turned completely to linux I am trying to reuse it once more.
I have successfully used inputattach with mtouch option to make the tablet work as said at the previous posts (movement only when pressing the first button either on mouse or stylus and no buttons working).

I've also used a calibration mask on the tablet itself to help calibrating and everything is fine.

Trying to reassign the buttons though... I can't reassign them. 
If I give xinput set-button-map "MicroTouch Serial TouchScreen" 0 1 2
The assignment doesn't change, so no buttons working.
My props are:
```
Device 'MicroTouch Serial TouchScreen':
        Device Enabled (117):   1
        Coordinate Transformation Matrix (119): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (242):     0
        Device Accel Constant Deceleration (243):       1.000000
        Device Accel Adaptive Deceleration (244):       1.000000
        Device Accel Velocity Scaling (245):    10.000000
        Evdev Axis Inversion (246):     0, 0
        Evdev Axis Calibration (247):   <no items>
        Evdev Axes Swap (248):  0
        Axis Labels (249):      "Abs X" (612), "Abs Y" (613)
        Button Labels (250):    "Button Unknown" (235), "Button Unknown" (235), "Button Unknown" (235), "Button Wheel Up" (123), "Button Wheel Down" (124)
        Evdev Middle Button Emulation (251):    0
        Evdev Middle Button Timeout (252):      50
        Evdev Wheel Emulation (253):    0
        Evdev Wheel Emulation Axes (254):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (255):    10
        Evdev Wheel Emulation Timeout (256):    200
        Evdev Wheel Emulation Button (257):     4
        Evdev Drag Lock Buttons (258):  0
```

Any help anyone?

---

