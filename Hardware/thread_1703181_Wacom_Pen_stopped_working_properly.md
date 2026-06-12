---
title: "Wacom Pen stopped working properly"
date: 2011-03-08
forum: Hardware
---

### Post by The Big Head One on 2011-03-08
So, I've been using my Wacom Pen in Ubuntu for some months, it was working great until the last time I used it (1 week ago, I think). I tried to use it today and it's not working properly. When I touch the tablet with the pen and then lift it, the cursor stops moving, even if I keep moving the pen (near the tablet, not touching it). The second problem is that it's not working in the left-handed mode like it was configured before. I tried to reconfigure it in /usr/lib/X11/xorg.conf.d/10-wacom.conf, but the file was empty, nothing was writen there. Then I saw that the wacom.conf file was /usr/share/X11/xorg.conf.d/50-wacom.conf for Ubuntu 10.10 or newer, but there was no /xorg.conf.d/50-wacom.conf in /usr/share/X11.

I tested my tablet in Windows, it's working properly there, and I'm using Ubuntu 10.10.

Thank you.

---

### Post by Favux on 2011-03-09
Hi The Big Head One,

The 50-wacom.conf should be in /usr/share/X11/xorg.conf.d/ in Maverick, that's the standard location.  The Lucid /usr/lib/X11/xorg.conf.d/ is a non-standard location they came up with because the Lucid 1.7 X server is actually a hybrid with an early version of 1.8 so Debian/Ubuntu could get rid of HAL and the .fdi files and go to xorg.conf.d and the .conf files.  /usr/share/X11/xorg.conf.d is where you add custom user .confs.  But don't try adding that directory in Lucid, it'll break things.

Does your 50-wacom.conf look normal?  If so the kernel update probably broke things.  What did you do before to get the Bamboo Pen working?  It is a CTL460 right?

Let's see what shows up in the *xinput list* output.

---

### Post by The Big Head One on 2011-03-09
The problem is: there's no /usr/share/X11/xorg.conf.d folder in my Ubuntu, so there's no 50-wacom.con :(

It was working great before. I think the first time I installed it I was using Ubuntu 10.04, and I think I used the 
"apt-get install xserver-xorg-input-wacom wacom-tools", and added 2 lines in /usr/lib/X11/xorg.conf.d/10-wacom.conf: Option "Rotate" "HALF" and Option "KeepShape" "on"

[FONT=Verdana]The [/FONT][I]xinput list shows:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                        id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)]


[/I]

---

### Post by Favux on 2011-03-09
Hmmm, let's see the output of:
```
xinput list-props "Wacom Bamboo 4x5 Pen"
```
in a terminal.  By the way it should say "Wacom Bamboo 4x5 Pen stylus".

There is no wacom-tools anymore.  There has to be a /usr/share/X11/xorg.conf.d directory in Maverick (10.10).  That's where the configuration .conf files are.  They were in /usr/lib/X11/xorg.conf.d in Lucid.

So this doesn't just appear to be a matter of not having the xserver-xorg-input-wacom package installed.  It should be by default in Maverick and it's what has the 50-wacom.conf.  It should show in Synaptic Package Manager as installed.

---

### Post by The Big Head One on 2011-03-09
Here's the output:

Device 'Wacom Bamboo 4x5 Pen':
    Device Enabled (142):    1
    Device Accel Profile (261):    0
    Device Accel Constant Deceleration (262):    1.000000
    Device Accel Adaptive Deceleration (264):    1.000000
    Device Accel Velocity Scaling (265):    10.000000
    Evdev Reopen Attempts (259):    10
    Evdev Axis Inversion (266):    0, 0
    Evdev Axis Calibration (267):    <no items>
    Evdev Axes Swap (268):    0
    Axis Labels (269):    "Abs X" (477), "Abs Y" (478), "Abs Pressure" (479), "None" (0)
    Button Labels (270):    "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Wheel Up" (146), "Button Wheel Down" (147), "Button Horiz Wheel Left" (148), "Button Horiz Wheel Right" (149)
    Evdev Middle Button Emulation (271):    2
    Evdev Middle Button Timeout (272):    50
    Evdev Wheel Emulation (273):    0
    Evdev Wheel Emulation Axes (274):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (275):    10
    Evdev Wheel Emulation Timeout (276):    200
    Evdev Wheel Emulation Button (277):    4
    Evdev Drag Lock Buttons (278):    0

And I checked in Synaptic and  xserver-xorg-input-wacom is installed

Here's the SS of my /usr/lib/X11/xorg.conf.d folder: [http://img155.imageshack.us/i/ss1mi.jpg/](http://img155.imageshack.us/i/ss1mi.jpg/)
And here's the SS of my /usr/share/X11 folder: [http://img405.imageshack.us/i/ss2ig.jpg/](http://img405.imageshack.us/i/ss2ig.jpg/)

---

### Post by Favux on 2011-03-10
Alright, having a 10-wacom.conf in /usr/lib/X11/xorg.conf.d sure makes it look like you are using Lucid (10.04) and not Maverick (10.10)  The list-props output shows that the Wacom stylus is on the evdev driver not the Wacom driver.  So either the Wacom driver isn't installed or the match lines in 10-wacom.conf aren't working.  Search Synaptic Package Manager for xserver-xorg-input-wacom and if it isn't installed install it and reboot.

Did you do an upgrade to Maverick from Lucid?  It's not looking like that worked if you did.

If not after installing the driver if the stylus isn't working let's check the 10-wacom.conf and see if the right keywords for the matches are in there.  Post the contents of 10-wacom.conf.

---

### Post by The Big Head One on 2011-03-10
Yes, my xserver-xorg-input-wacom is installed and I saw now that my Ubuntu is "Ubuntu 10.04 LTS - Lucid Lynx", but I'll upgrade it to 10.10 now, sorry for the wrong information. 

Surprisingly there's nothing in my 10-wacom.conf file @.@, it's empty.

---

### Post by Favux on 2011-03-10
That's why the stylus was on the evdev driver.  Evdev is a fail safe driver that picks up devices if nothing else does.  Since you don't have the match lines for a Wacom tablet in the a .conf or the the *Driver "wacom"* line for that matter since there is no 10-wacom.conf evdev tries to pick it up.  I think you've shed light on why a bunch of Bamboo Pens stopped working.  Something in the recent update removed the 10-wacom.conf without replacing it.  That shouldn't happen.

The question with Maverick like Lucid will be whether the default wacom.ko (usb kernel driver/module) works for the Bamboo Pen.  They haven't up till now.

---

### Post by The Big Head One on 2011-03-13
So, after I uploaded to 10.10, almost everything is working. The tablet works as intended, the **Option "Rotate" "HALF"** (to change to left-handed mode) works great, but when I try to put the [FONT=monospace][/FONT]**Option ****"KeepShape" "on"**, and after I restart my PC, when I'm using the tablet, my cursor stays on the edge of the monitor, whatever I do (moving the pen, touching the tablet with it and moving, etc), the cursor stays on the edge of the monitor.

I tried kde-config-tablet to see if I could activate the KeepShape there, but then, when I try to open it (sudo kcmshell4 kcm_tablet), it shows:

Error: "/var/tmp/kdecache-askasok" is owned by uid 1000 instead of uid 0.
Object::connect: No such signal QDBusAbstractInterface::tabletAdded()
Object::connect:  (receiver name: 'TabletWidget')
Object::connect: No such signal QDBusAbstractInterface::tabletRemoved()
Object::connect:  (receiver name: 'TabletWidget')
kcmshell(2621): DBus reply tabletAvailable failed 

And the GUI says:
"DBus connection to kded deamon not available! 
Please start the tablet deamon and try again.
The deamon is responsible for tablet detection and profile support."

---

### Post by Favux on 2011-03-13
KeepShape was just temporarily removed since it wasn't supported.  I think they're planning on adding it back at some point.  Other TwinView type Options were dropped by xf86-input-wacom 0.10.9.  Maverick has 0.10.8 as the default.  So KeepShape might or might not still be working for you.  Sounds like it isn't.  What do you need it for?  You can set the BottomX and Y Options to mimic the effect.

---

### Post by The Big Head One on 2011-03-13
My monitor is widescreen but my tablet isn't, isn't that the use **KeepShape "on"**, to "fix" this? How can I mimic the KeepShape using this Bottom X and Bottom Y?

Thank you :)

---

### Post by Favux on 2011-03-13
Yep, that's what KeepShape is for.

See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)  You figure out the monitor proportion and limit the tablet BottomX & Y to the same proportion.

---

### Post by bigfunkychiken on 2011-07-07
Sorry for the bump, but I really need a fix for this in Ubuntu 10.04 . Could somebody give me the default configuration file for the Wacom Bamboo Pen?
Thanks so much. I have the same problem as stated in the first post.

---

### Post by bigfunkychiken on 2011-07-07
Never mind, here is the fix:

```
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "KeepShape" "off"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection
```

Change KeepShape to on if you have a widescreen monitor.

---

### Post by The Big Head One on 2011-07-07
I think Keep Shape works with 10.04, but not with 10.10.

I have another problem now. My tablet was working great, and I don't know what the hell happened that it isn't working at all. I connect it, move the pen, but the cursor doesn't move.[B]

xserver-xorg-input-wacom[/B] is installed (I checked in Synaptic). I tried the command **gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf **and that was the output (as intended):

[B]Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Rotate" "HALF"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection[/B]

I tried the ***xinput list*** command, and that was the output:

[B]&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)][/B]

And after the **xinput list-props "Wacom Bamboo 4x5 Pen"** command, the output was:  **unable to find device Wacom Bamboo 4x5 Pen**.

So, any idea of what happened? My Ubuntu is 10.10 and the tablet was working flawlessly some weeks ago (under 10.10). I didn't do any great update or modification in my Ubuntu, just the usual ones that are recommended by the system. My tablet is a Wacom Pen btw, and it is working under Windows, so I don't think the problem is the Tablet.

Thank you.

---

### Post by Favux on 2011-07-07
The default wacom.ko (the usb kernel driver) in Maverick doesn't support Pen and Touches.  You must have either compiled one or installed one through a PPA.  When the new kernel came through for Maverick recently it would have installed the older, non-working wacom.ko.  That's why you don't see your Pen tablet in the *xinput list*, there is no usb communication.  You need to recompile a wacom.ko that works.  See part I. of the [[URL="ttp://ubuntuforums.org/showthread.php?t=1515562"]Bamboo P&T HOW TO]("ttp://ubuntuforums.org/showthread.php?t=1515562")[/URL].

---

### Post by The Big Head One on 2011-07-08
Thank you, it's working now =)

---

