---
title: "GXinput - GUI for XInput settings"
date: 2009-02-04
forum: Hardware
---

### Post by jolund on 2009-02-04
The new Xorg in jaunty changes a lot about how to config your input devices, and there is not yet very good tools for it. Mostly you have to use xinput and manual .fdi hacking.

I got tired of fiddling with the commandline xinput to make special settings on my input devices, so I decided to write my own UI for it, which exposes all the hidden xinput settings. I use this to enable middle mouse wheel emulation on my x300 amongst others. 

Here is a link: 
[http://dev.vostok6.net/gxinput](http://dev.vostok6.net/gxinput)

Mercurial repo at

[http://hg.vostok6.net/gxinput](http://hg.vostok6.net/gxinput)

Planned additions is generation of fdi rules and xinput commandlines. 
Comments, suggestions? Or event better, anyone wants to help add more stuff to the program?

---

### Post by Merlin2001 on 2009-11-06
Hello Joakim,

since I've been trying to disable the track stick (that's broken and making the mouse do funny things) on my Dell Latitude D800, I'm really interested in GXinput but am stuck trying to figure out how to run it.
I'm new to Ubuntu and haven't built a binary yet, which seems is necessary for GXinput to work - could you give me brief instructions on how to get GXinput to work?

I really appreciate the work you've done since I've spent quite some time searching for a way to easily disable the track stick (gsynaptics didn't work, mouse config dialog neither).

You could also just tell me the command to permanently disable the track stick (which I found out has id=7 using "xinput list") with xinput - then I would not need the GUI :)

Thanks in advance and greetings from Germany
Marcus Mangelsdorf

---

### Post by hskoglund on 2009-11-08
[FONT=Times New Roman]Hi, I'm also pretty new to Ubuntu and had the same problem with my Dell touchpad (ok it's working fine but I prefer it no to work), and xinput was the way to go for me.

You got the first step right, finding the number (7 in your case).

The command to disable your track stick should then be:
[/FONT]
[FONT=Courier New]xinput set-int-prop 7 "Device Enabled" 8 0

[FONT=Times New Roman]This should work fine for you until the next reboot.
To get a lasting effect, I put my (similar) xinput command in the list of
System->Preferences->Startup Applications.

Also note that the number 7 can and will change (it happened to me, i.e.
one day the touchpad was back again!). To really nail it, you need to
substitute the digit 7 for the device name string in the command. For me,
that meant changing the command line:

[/FONT][/FONT][FONT=Courier New][FONT=Times New Roman][FONT=Courier New]xinput set-int-prop 5 "Device Enabled" 8 0[/FONT]
to

[/FONT][/FONT][FONT=Courier New][FONT=Times New Roman][FONT=Courier New]xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 0
[FONT=Tahoma]
Hopefully this will work for you too.
Rgrds Henry
[/FONT][/FONT][/FONT][/FONT]

---

### Post by Merlin2001 on 2009-11-10
Hello Henry,

first of all: Thanks for your quick answer!
Since the thread was relatively old, I didn't really expect one from the original author, neither from somebody else ;)

Your guide was really good and easy to follow, can you tell me where you found the information about the use of xinput? (or what I am doing by selecting "(..) 8 0"?)

It seems like the Track Stick is (somehow) disabled now, since it doesn't move the mouse anymore, but it still kind of "blocks" the use of the touchpad - meaning that when the Stick is touched (or better to say: the keyboard in general - that's why it's so annoying...) I can't move the mouse using the touchpad. Like if the signal would still be recognized (blocking the touchpad) but kept from moving the mouse pointer.

Since you were able to get me a giant step further - do you maybe have any ideas concerning my (new *g*) problem?

Thanks again for your support!
Marcus

---

### Post by hskoglund on 2009-11-17
[SIZE=3][FONT=Times New Roman]To learn more about Xinput, for me it was mostly some trial-and-error.
Start by displaying all the properties for your device #7, like this:

xinput list-props 7

That property I mentioned before Device Enabled, or 98,
is maybe too heavy-handed, because, as you mentioned,
it disabled *all* of the functionality.

I mean you don't want to disable the touchpad, just the track stick. So perhaps you can try a different property to change, like "Stick Enabled" or similar. Look in the list.

Finally, about that (.. 8 0) settings, the 8 is just a guess (if 8 fails, then try 16 etc.) 
0 here means turn off the functionality, i.e. turn off "Device Enabled".

Rgrds Henry

[/FONT][/SIZE]

---

### Post by Merlin2001 on 2009-11-18
Hi Henry,

thanks for your advice. I tried messing around with xinput a bit and (thanks to Keir Thomas' Ubuntu Pocket Guide) found out that ```
man xinput
``` gives at least minimal help :)

But still I can't get a satisfying result:
The output of ```
xinput list-props "DualPoint Stick"
``` is the following:

```
Device 'DualPoint Stick':
    Device Enabled (89):    0
    Evdev Reopen Attempts (225):    0
    Evdev Axis Inversion (264):    0, 0
    Evdev Axis Calibration (265):    
    Evdev Axes Swap (266):    0
    Evdev Middle Button Emulation (267):    2
    Evdev Middle Button Timeout (268):    50
    Evdev Wheel Emulation (269):    0
    Evdev Wheel Emulation Axes (270):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (271):    10
    Evdev Wheel Emulation Timeout (272):    200
    Evdev Wheel Emulation Button (273):    4
    Evdev Drag Lock Buttons (274):    0
```where I manually set "Enabled" to 0 and "Reopen Attempts" to 0 (was 10).
(just to try if this has any influence on my problem *g*)

Unfortunately the problem is still unsolved though. The Touchpad is working (this is an extra device in xinput called "AlpsPS/2 ALPS DualPoint TouchPad") but randomly freezes if the Track Stick is touched (or I type on the keyboard)

May there be a way to completely "disconnect" (in a software way) the stick, maybe using the evdev driver or something?

In Windows there is a proprietary driver for the Touchpad/TrackStick combination where one can completely disable the TrackStick (because it does the same nonsense movement in Win when not disabled...)

Again, thanks for your answer and have a great week!
Marcus

---

### Post by Cruxic on 2009-12-05
Looks like a neat program, jolund.  Any plans to add configuration options for the _[fancy new pointer acceleration]("http://www.x.org/wiki/Development/Documentation/PointerAcceleration")_ code in X Server 1.6 (>=Jaunty)?

I'd be glad to help code this if you like.

---

### Post by peddanet on 2010-01-12
This site seems to be constantly down! Any Ideas how I can watch or download this project? Is it reliable, I did not find any other links to it! Is there a doc?

> **jolund said:**
> The new Xorg in jaunty changes a lot about how to config your input devices, and there is not yet very good tools for it. Mostly you have to use xinput and manual .fdi hacking.

I got tired of fiddling with the commandline xinput to make special settings on my input devices, so I decided to write my own UI for it, which exposes all the hidden xinput settings. I use this to enable middle mouse wheel emulation on my x300 amongst others. 

Here is a link: 
[http://dev.vostok6.net/gxinput](http://dev.vostok6.net/gxinput)

Mercurial repo at

[http://hg.vostok6.net/gxinput](http://hg.vostok6.net/gxinput)

Planned additions is generation of fdi rules and xinput commandlines. 
Comments, suggestions? Or event better, anyone wants to help add more stuff to the program?

---

### Post by GenPFault on 2013-01-17
Archive.org has [a copy]("http://web.archive.org/web/20091122105236/http://dev.vostok6.net/gxinput/browser").

---

### Post by Crafty Kisses on 2013-01-18
Haha thanks

---

### Post by Redsandro on 2013-02-20
Thanks, I just noticed the original link wasn't working anymore. :P

I can't believe we still don't have BASIC stuff like xinput gui, screen calibration, joypad control panel, either out of the box or AT ALL, while the Canonical/Ubuntu team pays devs good money to reinvent wheels such as Gnome Shell -> Ubuntu Unity, Xorg.conf -> [Custom display server]("http://www.omgubuntu.co.uk/2013/02/canonical-working-on-new-display-server"), etc.

Am I the only one that understands how basic stuff like this separates OSX/Windows from Ubuntu? 2 out of 3 people I install Ubuntu for on their computers end up wanting to go back to their old OS because they can't do basic stuff like this.

In both Windows and OSX you can tick a box to say that you are left-handed. In Ubuntu you have to probe all the xinput options, guess about the meaning of values, and write a custom script like this:
```
#!/usr/bin/env bash

WACOM_STYLUS=`xinput --list --short | grep -m1 "Wacom Bamboo 2FG 4x5 Finger touch" | cut -f2 | cut -d= -f2`
WACOM_ERASER=`xinput --list --short | grep -m1 "Wacom Bamboo 2FG 4x5 Pen stylus"   | cut -f2 | cut -d= -f2`
WACOM_TOUCH=` xinput --list --short | grep -m1 "Wacom Bamboo 2FG 4x5 Pen eraser"   | cut -f2 | cut -d= -f2`

xinput --set-prop $WACOM_STYLUS "Wacom Rotation" 3
xinput --set-prop $WACOM_ERASER "Wacom Rotation" 3
xinput --set-prop $WACOM_TOUCH  "Wacom Rotation" 3
``` Why doesn't Canonical put a tiny bit of resources in this. It's pretty retarded.

---

### Post by Favux on 2013-02-20
Hi Redsandro,

Couple of quibbles.  A Wacom tablet may not be the best example.  While you can use xinput you do not need to.  Besides it makes the script unnecessarily complicated.  This works fine:
```
#!/bin/sh

xsetwacom set "Wacom Bamboo 2FG 4x5 Pen stylus" Rotate ccw
xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Rotate ccw

```
And you only need touch because it is a usb device (touch is a separate parent device).  If it was a serial device you would only need the stylus line to get the eraser and touch rotated also.

More to your point you can skip a script and use the Gnome Wacom Graphics Tablet applet in System Settings to set your tablet left handed.  I believe the KDE Wacom system tool has a left handed setting also.

---

### Post by Redsandro on 2013-02-20
Wow, you seem to know a lot more by heart than I do after pretty much an hour of googling and fiddling.

You by any chance happen to know how I can set the buttons on the tablet to do stuff? There is a buttons option for all 4, and I want to be able to toggle touch and right-/double-click or sth, but I googled around the world and got distracted by lolcats and now I am reading python tutorials. That escalated quickly.

Anyway, apart from the example, I am still baffled by the lack of usabilitytools for non-technical people. :)

PS - I cannot find a Wacom control panel in Synaptic? I did manage to get some keyboard touches out of the tool you specified though, but no mouse clicks yet. Also, my Bamboo has 4 buttons. I can only set 3 buttons, of which only 2 actually work.

-edit- Since this is officially kinda offtopic, I've moved the Wacom talk to a [new thread]("http://forums.linuxmint.com/viewtopic.php?f=49&t=126282"). :)

---

### Post by Favux on 2013-02-20
Followed you to the new thread.

---

