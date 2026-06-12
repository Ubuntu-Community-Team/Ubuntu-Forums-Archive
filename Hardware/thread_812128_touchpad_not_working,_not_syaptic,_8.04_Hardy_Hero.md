---
title: "touchpad not working, not syaptic, 8.04 Hardy Heron"
date: 2008-05-29
forum: Hardware
---

### Post by raequin on 2008-05-29
Hi, all. I have been trying since installation of Hardy to get my touchpad working well when I type. I have edited xorg.conf, as shown below. Syndaemon has no effect when I run it. Also, System->Preferences->Mouse changes nothing, even when I uncheck the box "enable touchpad."

There are only two things that I can do to affect the touchpad, use Fn+F7 that is the touchpad on / off button that came with the laptop (an Acer), or use Mousetweaks pointer capture on the panel.

I would like to be able to either turn off the touchpad with either keyboard shortctus or by terminal command (which maybe I could bind to a keyboard shortcut), or get syndaemon working so that I can type without worrying about the touchpad.

Here is a part of xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
# Option "MaxTapTime" "0"
EndSection

"MaxTapTime" did nothing either, so I commented it out. Nothing I do in gsynaptics has any effect.

I tried installing gsynaptic, and received the following message:

sudo apt-get install gsynaptic
...
Reading state information... Done
Note, selecting synaptic instead of gsynaptic
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also tried the following line instead of what is posted above, in xorg.conf:
Option "SHMConfig" "true"

Please help me get this working, syndaemon hopefully, because it really makes Ubuntu not as useful as Windows --- maybe.

ps - I guess since it's not syaptic, the vertical scrolling is not working nor is the rocker button --- the thing that's like the wheel on a mouse.

---

### Post by wolfen69 on 2008-05-30
i found [THIS]("http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/") hope it helps.

---

### Post by wolfen69 on 2008-05-30
[HERE]("http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/") is another one.

---

### Post by raequin on 2008-05-30
> **wolfen69 said:**
> i found [THIS]("http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/") hope it helps.

This has no effect.  I appreciate very much your interest.  I already tried editing xorg.conf then using syndaemon and also the command suggested in the link you sent, synclient TouchpadOff=1.

I would think that Hardy is unable to modify the behavior of my touchpad if it were not for the pointer capture program I mentioned in the original post.  Now, if I could just figure out how it does it ...

---

### Post by strabes on 2008-05-30
Are you restarting your xserver after you edit your xorg.conf? Are you sure you have a synaptics touchpad? What is wrong with simply using the keyboard shortcut built into your laptop?

---

### Post by ugm6hr on 2008-05-31
I'm unclear on what you have done so far, but thought I'd try and help.

Couple of simple things to try:

In this section - add the line in bold:
```
Section "Module"
	Load		"glx"
	**Load		"synaptics"**
EndSection
```

Make sure you restart X after each change.

The fact that MaxTapTime doesn't turn tapping off suggests that the synaptics driver is not being used at all.  The first suggestion has helped me resolve this with prior versions of Ubuntu (although it just works in Hardy).

EDIT:
Sometimes it is as simple as putting the touchpad section above the mouse section in xorg, and adding this to the Touchpad section (and removing from mouse):
```
	Option		"CorePointer"
```

---

### Post by raequin on 2008-05-31
> **ugm6hr said:**
> I'm unclear on what you have done so far, but thought I'd try and help.

Couple of simple things to try:

In this section - add the line in bold:
```
Section "Module"
	Load		"glx"
	**Load		"synaptics"**
EndSection
```

Make sure you restart X after each change.

The fact that MaxTapTime doesn't turn tapping off suggests that the synaptics driver is not being used at all.  The first suggestion has helped me resolve this with prior versions of Ubuntu (although it just works in Hardy).

EDIT:
Sometimes it is as simple as putting the touchpad section above the mouse section in xorg, and adding this to the Touchpad section (and removing from mouse):
```
	Option		"CorePointer"
```

Putting the touchpad section above the mouse section had no effect.  Moving the "CorePointer" option from mouse to touchpad caused the touchpad to stop working.

xorg.conf did not have a "Module" section.  I added one, with one line (Load "synaptics"), but that had no effect.

---

### Post by ugm6hr on 2008-05-31
You are certain it's a Synaptics touchpad?  ALPS pads often (but not always) work with the same driver.

And sorry about the CorePointer thing - you can't have CorePointer and SendCoreEvents in the same device.

Presumably you have section similar to this too:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

---

### Post by raequin on 2008-05-31
I am not at all certain that it is a synaptics touchpad, although the documentation, i.e. user manual that came as a pdf on vista mentions synaptic.  It is an Acer laptop.

As to the "ServerLayout" section in xorg, it is exactly as you guessed.

---

### Post by raequin on 2008-06-02
* bump *

---

### Post by raequin on 2008-06-03
bump

---

### Post by Ceadda on 2008-06-17
bump

---

### Post by eynestyne on 2008-06-17
Had a similiar problem. Touchpad partially gave out after installing video card driver. The issue was in the xconf file.

I modified serverlayout to point to the pad:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad"
EndSection
```

and added the section below:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

```

Hope this helps

---

### Post by Samsam08 on 2008-06-23
I have the same problem. It has something to do with Synclient I guess. Whenever I try synclient -l in the terminal I get this message:
 "Can't access shared memory area. SHMConfig disabled?"
Even though SHMConfig is set correctly.

I tried all the options mentioned here and on other forums but nothing worked. The only thing that had any effect at all was the Option "Corepointer"added to the touchpad chapter which caused both touchpad and mouse to be disabled, it took me quite a while to be able to get back in the computer after that!

I believe the experts are working on the problem, so for now I give up. But if anyone has a brilliant idea, please let me know. All I need is a to make a key combination to temporarily shut of the touchpad (and no, adding the option touchpadoff 1 doesnot do the trick)

---

### Post by Samsam08 on 2008-06-23
Oh, and by the way when I try System / preferences / touchpad I always get this error message:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

And yes, SHMConfig is set that way

Maybe it's my laptop, it's a custom built notebook based on the Compal fl92 configuration. I can't find out exactly what kind of touchpad it is.

---

### Post by kronictokr on 2008-11-25
FIRST
edit your xorg.conf, so that SHM line is above the scroll option
change the wording in the scroll option to match mine, (i had to )
and make sure!! the whole section is placed above the mouse input section
like so

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option          "SHMConfig"             "on"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection



SECONDLY

In a terminal type:

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

Put this into the file:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

Save and close that file, reboot
after i did this things work great!!
 
hope this helps

---

