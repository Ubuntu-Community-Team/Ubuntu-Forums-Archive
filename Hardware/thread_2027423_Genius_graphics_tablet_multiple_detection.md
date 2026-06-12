---
title: "Genius graphics tablet: multiple detection"
date: 2012-07-16
forum: Hardware
---

### Post by ArsThaumaturgis on 2012-07-16
I'm trying to get my graphics tablet working, but am finding myself struggling, even after various searches and experiments.

From what I've gathered thus far, it seems that I may have two problems: first, that my tablet is being detected twice, and second, that it appears to be being detected as a either a mouse or a touchpad.  (I'm not confident that the latter is in fact a problem; it does, however, look like a potential issue.)

_My computer:_
Gigabyte Q2005 netbook
Intel Atom N550 CPU
2GB RAM

_My tablet:_
Genius WizardPen 5x4

_My Ubuntu version:_
11.1

_Symptoms:_
The tablet appears to work at first, with the cursor moving to follow.  However, after the first tap, said tap seems to never be released.  The cursor can be moved if the nib is touching the tablet, but this effects dragging (as one might expect).  This state seems to remain until the tablet is disconnected and next reconnected.

_What I've tried and learned thus far:_

xinput -list shows two entries for my tablet, both simply called "  TABLET DEVICE" (including the two spaces before "TABLET", and entirely capitalised).

Xorg.0.log (in /var/log/) shows two detections of my tablet; I note the following lines:
[LIST]
[*]The first detection:
[LIST]
[*]```
[   255.553] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event12)
[   255.553] (**)   TABLET DEVICE: Applying InputClass "evdev pointer catchall"
```
[*]```
[   255.555] (II) XINPUT: Adding extended input device "  TABLET DEVICE" (type: MOUSE)
```
[/LIST]
 
[*]The second detection, just after the first:
[LIST]
[*]```
[   255.560] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event11)
[   255.560] (II) No input driver/identifier specified (ignoring)
[   255.565] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/mouse2)
[   255.565] (II) No input driver/identifier specified (ignoring)
[   255.571] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/mouse3)
[   255.572] (II) No input driver/identifier specified (ignoring)
[   255.581] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event13)
[   255.581] (**)   TABLET DEVICE: Applying InputClass "evdev pointer catchall"
```
[*]```
[   255.582] (II) XINPUT: Adding extended input device "  TABLET DEVICE" (type: TOUCHPAD)
```
[/LIST]
 
[*](There is more in the log file, but I leave the remaining lines out for the sake of some semblance of brevity; I'm happy to post the full set if asked, I believe.)
[/LIST]
From what I've read, there should be some way of preventing duplicate detections and adjusting the behaviour of the tablet; most of what I've found seems to have indicated the removal of a section in xorg.conf - which I also gather doesn't exist in 11.1.  How do I remove lines from a file that doesn't exist, or am I supposed to create it and add something particular to it, presuming that it overrides whatever is currently detecting my tablet?  Am I supposed to edit some other file elsewhere, and if so, which?  I have attempted some changes to files found in xorg.conf.d, of I recall correctly, to no apparent effect thus far...

My thanks for any aid given on this. ^_^

---

### Post by Favux on 2012-07-16
Hi ArsThaumaturgis,

Welcome to Ubuntu forums!

What is suppose to be happening, if your model is supported in the kernel, is the kernel driver is suppose to mark the two device nodes you are seeing in Xorg.0.log (or the **xinput list** command if you ran it) as tablet and mouse and/or keyboard.  Mouse if you have tablet mouse (or your model tablet supports one even if you don't have it) and keyboard if you have tablet buttons.  Then the appropriate evdev snippet in 10-evdev.conf (/usr/share/X11/xorg.conf.d) is suppose to match to that.  In Xorg.0.log you would be able to tell that because the appropriate identifier would be associated with the setup.  Which would be "evdev tablet catchall" not "evdev touchpad catchall".

Since you are matching to touchpad rather than the tablet snippet it looks like your tablet isn't one of the currently supported models:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)
Run **lsusb** in a terminal to find out which OEM and Product ID you have.

You could try manually matching in a custom .conf in /etc/X11/xorg.conf.d.  You probably would also have to supply coordinates from say xinput_calibrator.

---

### Post by ArsThaumaturgis on 2012-07-16
Thank you for the welcome, and for your help! ^_^

Hmm...  This is odd.  Based on the Support Status page to which you linked, and borne up by the results of the lsusb command, it looks as though my tablet should be supported.  To be specific, it's a Wizardpen 5x4, which the page gives as being a "UC-Logic Tablet WP5540U"; the same result seems to be given by lsusb.

(The output of lsusb:
```
Bus 002 Device 003: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U
```)

I see that my 10-evdef.conf file does seem to include a "tablet catch-all" InputClass; is it still worth trying a custom conf file, and if so, what should go into it?

[edit] A quick thought: is it plausible that other pointing devices might be interfering?  I have a wireless USB mouse that operates as my main pointing device, and a touchpad built into the netbook that I generally turn off.

---

### Post by Favux on 2012-07-16
That is odd, it should be supported in Oneiric.

Since the evdev:
```
MatchIsTablet "on"
```
isn't working let's try another match.  That may be a bug.

Say:
```
Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```
I'm guessing the keyword "WP5540U" is what you see when you run **xinput list**.  Using:
```
gksudo gedit /etc/X11/xorg.conf.d/52-evdev.conf
```
You might have to make the xorg.conf.d directory,

But we also need to deal with the mouse snippet so we get unique matches.  Since that does appear to be using the correct snippet maybe that match is working.  Hope so.
```

Section "InputClass"
        Identifier "evdev tablet options"
	MatchIsPointer "on"
        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```
Give it a shot and let's see what happens.  Maybe the snippets should be reversed.  The info. does show there are no buttons on that Genius tablet but it can come with a mouse.

---

### Post by ArsThaumaturgis on 2012-07-16
I've only tried it as you put it there thus far, but no apparent effect has been had: the same symptoms present, and the log file still seems to indicate that the "evdev pointer catchall" is being used. :/

In case I misinterpreted your instructions, what I did was this:

[LIST]
[*]Create a folder named "xorg.conf.d" in the folder /etc/X11/
[LIST]
[*]There was already a folder by that name in /usr/share/X11/, I believe, to which no changes were been made.
[/LIST]
[*]In the new folder, a file named "52-evdev.conf" was created, into which the contents of your last code section were pasted, but only the contents of that section, and including all hash-marks.
[*]The computer was restarted, and the tablet plugged in (after startup).
[/LIST]

---

### Post by Favux on 2012-07-16
Sounds correct.

/usr/share/X11/xorg.conf.d is for the Distro

/etc/X11/xorg.conf.d is for the user's custom .conf files

Try reversing the snippets then.  That may be needed to distinguish between the tablet and mouse.  Could also remove the comment (#) from before the MatchIsTablet line, but that didn't work before so probably not going to work now.

---

### Post by ArsThaumaturgis on 2012-07-16
No apparent change, I'm afraid, with both the sections reversed and the line uncommented. :/

Thank you for the explanation of the directories.  I'll confess that the directory naming system has been a frustration for me since switching to Ubuntu; in particular, I either find the names non-indicative or don't know the logic behind them, making it difficult to predict where I should look for a given file. :/

---

### Post by Favux on 2012-07-16
Sure.  They tell me the unix/linux directory is actually a thing of logical beauty.  It does take a bit of getting used to for sure.

Let's see if we can tell evdev it is a tablet by telling it Mode is Absolute so it knows it has absolute not relative axes.  So add this option to the tablet snippet:
```

Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "Mode" "Absolute"
EndSection

Section "InputClass"
        Identifier "evdev mouse options"
	MatchIsPointer "on"
        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

```
I also changed the mouse identifier to say mouse not tablet.  Are we matching with the current "WP5540U" match?  Does the identifier for the mouse change to mouse in Xorg.0.log?  Is "WP5540U" in the **xinput list** output?

---

### Post by ArsThaumaturgis on 2012-07-16
Still no change, I'm afraid. :/

As to the logs, my apologies - I meant "no change" to include that the log files seemed to be showing the same results as well, including the name "  TABLET", the dual detection and the use of "evdev pointer catchall".  It really doesn't look as though these new entries are being matched. :/

As to xinput, it simply identifies the tablet as "  TABLET" - unless there's a way to get more information.

lsusb, however, does seem to idientify it as "UC-Logic Technology Corp. Tablet WP5540U" - but then that was the case before the new file, I seem to recall.

---

### Post by Favux on 2012-07-16
Given that let's try a more generic match then.
```
Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
#        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "Mode" "Absolute"
EndSection

Section "InputClass"
        Identifier "evdev mouse options"
	MatchIsPointer "on"
	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
#        MatchProduct "WP5540U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```

Edit:  Oops I just caught **xinput list** output just has " TABLET".  Can you post the output of that command?  If that's so we've found the bug.

---

### Post by ArsThaumaturgis on 2012-07-16
xinput -list:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB RECEIVER                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; FSPPS/2 Sentelic FingerSensingPad           id=13    [slave  pointer  (2)]
&#9116;   &#8627;   TABLET DEVICE                             id=14    [slave  pointer  (2)]
&#9116;   &#8627;   TABLET DEVICE                             id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


```The second is likely my USB mouse and the third presumably my netbook's built-in touchpad, although the latter is disabled at the moment.  The two "  TABLET" entries seem to appear and disappear together as the tablet is connected and disconnected.

[edit]
Since you seem to think that the xinput output is a good avenue for investigation I haven't yet tried the new InputClass lines from your most recent post before this.

---

### Post by Favux on 2012-07-16
Thanks for the list.  Yep the keyword we should have been using was "TABLET".  Try that instead of "WP5540U".

Clearly the usb descriptor for the tablet is mangled.  At least it looks to be so. It should look more like:
```
UC-LOGIC Tablet WP1700U
```
in **xinput list** I would think.  The question is why.

---

### Post by ArsThaumaturgis on 2012-07-16
Ah!  Now we seem to be making some progress! ^_^

First of all, the tablet's behaviour is unchanged.

More promising, however, is that the new InputClasses seem to be being detected.  Unfortunately, the "pointer catchall" InputClasses seem to have remained alongside them, and we may have picked up a new detection - I'm not sure that I'm reading this correctly.  Let me paste in my log file results (my apologies for their length :/):

```

[   129.126] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event12)
[   129.126] (**)   TABLET DEVICE: Applying InputClass "evdev pointer catchall"
[   129.126] (**)   TABLET DEVICE: Applying InputClass "evdev tablet options"
[   129.127] (**)   TABLET DEVICE: Applying InputClass "evdev mouse options"
[   129.127] (II) Using input driver 'evdev' for '  TABLET DEVICE'
[   129.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   129.127] (**)   TABLET DEVICE: always reports core events
[   129.127] (**)   TABLET DEVICE: Device: "/dev/input/event12"
[   129.127] (--)   TABLET DEVICE: Found 3 mouse buttons
[   129.127] (--)   TABLET DEVICE: Found scroll wheel(s)
[   129.127] (--)   TABLET DEVICE: Found relative axes
[   129.127] (--)   TABLET DEVICE: Found x and y relative axes
[   129.127] (II)   TABLET DEVICE: Configuring as mouse
[   129.128] (II)   TABLET DEVICE: Adding scrollwheel support
[   129.128] (**)   TABLET DEVICE: YAxisMapping: buttons 4 and 5
[   129.128] (**)   TABLET DEVICE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   129.128] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input16/event12"
[   129.128] (II) XINPUT: Adding extended input device "  TABLET DEVICE" (type: MOUSE)
[   129.128] (II)   TABLET DEVICE: initialized for relative axes.
[   129.128] (**)   TABLET DEVICE: (accel) keeping acceleration scheme 1
[   129.128] (**)   TABLET DEVICE: (accel) acceleration profile 0
[   129.129] (**)   TABLET DEVICE: (accel) acceleration factor: 2.000
[   129.129] (**)   TABLET DEVICE: (accel) acceleration threshold: 4
[   129.132] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/mouse2)
[   129.132] (II) No input driver/identifier specified (ignoring)
[   129.133] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event11)
[   129.134] (**)   TABLET DEVICE: Applying InputClass "evdev tablet options"
[   129.134] (II) Using input driver 'evdev' for '  TABLET DEVICE'
[   129.134] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   129.134] (**)   TABLET DEVICE: always reports core events
[   129.134] (**)   TABLET DEVICE: Device: "/dev/input/event11"
[   129.134] (WW)   TABLET DEVICE: Don't know how to use device
[   129.164] (EE) PreInit returned 8 for "  TABLET DEVICE"
[   129.164] (II) UnloadModule: "evdev"
[   129.164] (II) Unloading evdev
[   129.165] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/mouse3)
[   129.166] (II) No input driver/identifier specified (ignoring)
[   129.167] (II) config/udev: Adding input device   TABLET DEVICE (/dev/input/event13)
[   129.167] (**)   TABLET DEVICE: Applying InputClass "evdev pointer catchall"
[   129.168] (**)   TABLET DEVICE: Applying InputClass "evdev tablet options"
[   129.168] (**)   TABLET DEVICE: Applying InputClass "evdev mouse options"
[   129.168] (II) Using input driver 'evdev' for '  TABLET DEVICE'
[   129.168] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   129.168] (**)   TABLET DEVICE: always reports core events
[   129.168] (**)   TABLET DEVICE: Device: "/dev/input/event13"
[   129.169] (--)   TABLET DEVICE: Found 3 mouse buttons
[   129.169] (--)   TABLET DEVICE: Found absolute axes
[   129.169] (II) evdev-grail: failed to open grail, no gesture support
[   129.169] (--)   TABLET DEVICE: Found x and y absolute axes
[   129.169] (--)   TABLET DEVICE: Found absolute touchpad.
[   129.169] (II)   TABLET DEVICE: Configuring as touchpad
[   129.169] (**)   TABLET DEVICE: YAxisMapping: buttons 4 and 5
[   129.169] (**)   TABLET DEVICE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   129.170] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input17/event13"
[   129.170] (II) XINPUT: Adding extended input device "  TABLET DEVICE" (type: TOUCHPAD)
[   129.170] (**) Option "Mode" "Absolute"
[   129.170] (II)   TABLET DEVICE: initialized for absolute axes.
[   129.171] (**)   TABLET DEVICE: (accel) keeping acceleration scheme 1
[   129.171] (**)   TABLET DEVICE: (accel) acceleration profile 0
[   129.171] (**)   TABLET DEVICE: (accel) acceleration factor: 2.000
[   129.171] (**)   TABLET DEVICE: (accel) acceleration threshold: 4

```

---

### Post by Favux on 2012-07-16
It would probably be better if you just right clicked on it and selected Compress and then just attached it to your next post.  Somtimes lines aren't grouped together and can help tell the story.

That is confusing.  It looks like event12 is the mouse and event13 is the tablet.  If the tablet is event11 then the Absolute option is confusing it.
```
[   129.134] (**)   TABLET DEVICE: Device: "/dev/input/event11"
[   129.134] (WW)   TABLET DEVICE: Don't know how to use device
[   129.164] (EE) PreInit returned 8 for "  TABLET DEVICE"
[   129.164] (II) UnloadModule: "evdev"
[   129.164] (II) Unloading evdev
```
But we see Absolute axes for the touchpad now.  Were we seeing that before?  Try changing event* to event11 in the tablet snippet and see what happens.  Also try event11 for the mouse and event13 for the tablet.  You get the idea.

When doing a restart the event number can change which is the problem.  So don't hot plug and see if the event numbers are relatively stable for you.

The other option I suppose is to write a udev rule and add tablet to the enviroment for the tablet node.  I assume that is how the usb descriptor is labeling them mouse and tablet.  Or should be labelling it tablet anyway.

---

### Post by ArsThaumaturgis on 2012-07-16
Fair enough; it's pretty late here, so I'm going to leave this for tonight and return in the new day, I intend.

Thank you for all of your help thus far - I'll hopefully report back tomorrow!

---

### Post by ArsThaumaturgis on 2012-07-17
All right, here are my latest results:

I tried the change to events -11 and -13, only to find that with the tablet plugged in at startup it seemed to be looking for event6 and mouse1, so I tried those.  With those specified, it seems to find the custom InputClasses, but not know what to do with them, falling back on the "evdev pointer catchall".

I haven't yet tried the udev rule, as I don't yet know what that is or how to instate it. ^^;

My current 52-evdev.conf looks like this now:
```
Section "InputClass"
        Identifier "evdev tablet options"
#    MatchIsTablet "on"
        MatchProduct "TABLET DEVICE"
        MatchDevicePath "/dev/input/event6"
        Driver "evdev"
        # Apply custom Options below.
    Option "Mode" "Absolute"
EndSection

Section "InputClass"
        Identifier "evdev mouse options"
    MatchIsPointer "on"
        MatchProduct "TABLET DEVICE"
        MatchDevicePath "/dev/input/mouse1"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```My latest Xorg.0.log should be attached to this post.

[edit]
Hmm... I've just noticed in the above code block that I seem to have a mixture of tabs and spaces - is that a potential problem?

---

### Post by Favux on 2012-07-17
It looks like event7 is the mouse and event8 is the tablet.  7 seems to set up fine and 8 although it calls it a touchpad has absolute axes which is what a tablet should have.

The mouse# or mouse by-path are spurious, I'm pretty sure.  So you shouldn't need to try them.  Notice it says 'Inappropriate ioctl for device'.

Try running:
```
cat /proc/bus/input/devices
```
and posting the output.  That should let you see the available event numbers for you to assign in the .conf.

---

### Post by ArsThaumaturgis on 2012-07-17
Here is the output.  I note that it seems to have three entries for the tablet.

---

### Post by Favux on 2012-07-17
Sure enough.  So that output was useful.

Hmm.  You don't have a tablet mouse correct?  There are no buttons on the tablet frame/bezel correct?

---

### Post by ArsThaumaturgis on 2012-07-17
I'll confess that I'm not entirely sure of what a "tablet mouse" is - I'm guessing that it's a special mouse designed to be used on the tablet surface?  Is so, then no, I don't have one.  As to buttons, the only ones that my tablet has are on the pen.

---

### Post by Favux on 2012-07-17
For tablet mouse and more fun info. on your tablet see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_WP5540U](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_WP5540U)

Given there is no mouse or buttons let's try to get some udevadmn info. from the events.  So run:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event6)
```
using whatever event# **cat /proc/bus/input/devices** is currently giving for the section that doesn't have mouse.  Then repeat for the two sections that say mouse using their event#'s.

Let's try to find out some more detail on the issue.  Plus we need the info. if we plan to make a udev rule.


Also let's change the .conf file.  Since we don' need to worry about anything but the pen/digitizer.
```
Section "InputClass"
        Identifier "evdev ignore tablet mouse"
	MatchIsPointer "on"
        MatchProduct "TABLET DEVICE"
        MatchDevicePath "/dev/input/mouse*"
        Driver "evdev"
	Option "Ignore" "on"
EndSection

Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "TABLET DEVICE"
#	MatchDevicePath "/dev/input/event6"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "Mode" "Absolute"
EndSection
```
You can go back to using event# if need be but since it can change we'd like to avoid that if possible.

---

### Post by ArsThaumaturgis on 2012-07-17
I've made the changes to the conf file (and restarted in case that did it - it didn't), and the results of the three udevadm calls should be in the attached zip file.

---

### Post by Favux on 2012-07-17
Assuming the matches still look good in Xorg.0.log let's try one last thing.  We'll try to specify the coordinates.  So add the Calibration option to the tablet snippet:

X max = 2000 LPI x 5.5 inches = 11000
Y max = 2000 LPI x 4 inches = 8000
```
Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "TABLET DEVICE"
#	MatchDevicePath "/dev/input/event6"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "Mode" "Absolute"
	Option "Calibration" "0 11000 0 8000"
EndSection
```
I don't think commenting out the Mode option will get us anything but you might want to try that also.


We struck out with the udevadm info.  There is nothing in there to discriminate between the 3.  I really don't want to look at a full udevadm dump.  You can see on the tablet information page the descriptors do tell the system the Interface is Tablet and the Usage is Stylus.

I think looking at the descriptors on the tablet page one mouse event is the actual cursor/pointer and the other the button.  Looks like there are suppose to be two event nodes for it.

---

### Post by ArsThaumaturgis on 2012-07-17
I haven't yet tried commenting out the "mode" option, but the  coordinates seem to just change the mapping from tablet to screen  (making a section at the top-left corner of the tablet cover the entire  screen), as I suppose is to be expected.

As to the log, I notice two things:
1) The line "(WW)   TABLET DEVICE: Don't know how to use device" seems  to still be present for the first detection; after this it seems to fall  to using both the evdev catch-all and the "tablet options" InputClasses
2) Both the detection as mouse and as touchpad seem to ignore the mouse  event as expected, but then register for an event instead, the former  using the catch-all and "tablet options" as above and the latter just  using the catch-all

The log file should be attached to this post in cast you want to take a look at it.

I'm likely off for the night, however, so I'll return again tomorrow, I intend - thank you for your patience and aid thus far. ^_^

---

### Post by Favux on 2012-07-17
Fine, I'll have a look and talk to you tomorrow.

The coordinate option actually affecting things would seem to indicate we've got the correct event and the options working on it.

---

### Post by ArsThaumaturgis on 2012-07-18
Hmm...  The plot thickens.

I've just discovered that if I touch the pen only lightly, I can drag, pick up the pen, and continue normally.  It's only when I apply a little more pressure that the cursor starts to "stick".

I've now also tried my tablet on a Windows machine, thinking that it might have begun malfunctioning since last I used it.  On that machine it appeared to have a similar problem at first: light touches seemed to work properly, but firmer strokes resulted in no movement, with the light on the tablet not turning on in those cases.  However, after a short while (specifically, when I wanted to show someone else! XD) it started to work properly.

There are some noteworthy differences, I believe:
1) On Ubuntu, firmer strokes do drag the cursor, but seem to prevent the release from being detected.  Under Windows, firmer strokes at first did not produce a response at all.
2) On Ubuntu, the light on the tablet seems to always respond.  On Windows, it didn't respond during the failed strokes.
3) On Windows the tablet started to work properly after a time.  On Ubuntu, it doesn't seem to rectify itself.

So, I have two further thoughts:
1) This tablet is rather old, the pen is sometimes a little dodgy anyway, and at least once it has had its cable shortened.  Despite working under Windows, it's entirely possible that the tablet is at least partially the problem.
2) Regarding the multiple detections: From what I've read elsewhere, my symptoms are the same as those that others have had when the tablet is detected more than once, and in their cases (back when xorg.conf was present by default, I think) I think that I recall that preventing one of these detections solved the problem.

---

### Post by Favux on 2012-07-18
> I've just discovered that if I touch the pen only lightly, I can drag, pick up the pen, and continue normally. It's only when I apply a little more pressure that the cursor starts to "stick".
Wow!  Great, the silly thing now "works" in linux.
> I've now also tried my tablet on a Windows machine, thinking that it might have begun malfunctioning since last I used it. On that machine it appeared to have a similar problem at first: light touches seemed to work properly, but firmer strokes resulted in no movement, with the light on the tablet not turning on in those cases. However, after a short while (specifically, when I wanted to show someone else! XD) it started to work properly.

Ah ha!  There is a hardware issue!
> This tablet is rather old, the pen is sometimes a little dodgy anyway, and at least once it has had its cable shortened.
While the connection at wherever the cable was shortened may now be an issue my question now is:  When did you last put a new battery in the pen?

Of course a secondary question is did anything we have done so far actually help?  Ouch.

> 2) Regarding the multiple detections: From what I've read elsewhere, my symptoms are the same as those that others have had when the tablet is detected more than once, and in their cases (back when xorg.conf was present by default, I think) I think that I recall that preventing one of these detections solved the problem. 
I think you are talking about an old issue when the WizardPen driver was the X driver for those tablets.  The WizardPen driver couldn't handle the mousue node(s).  And that was back when the xorg.conf.d .conf files were new.  It wasn't clear that:
```
Option "Ignore" "on"
```
was what you were suppose to use in those situations so DoctorMO invented the:
```
Driver ""
```
line as a substitute.  But it worked and does the same thing.

---

### Post by ArsThaumaturgis on 2012-07-18
> Wow!  Great, the silly thing now "works" in linux.
Well, as long as I don't apply more than the lightest force. :P

> Ah ha!  There is a hardware issue!
It is looking more  and more like it. :/

That said, it does (more or less) work under Windows, so there's presumably some relevant difference on the OS or software side...

> While the connection at wherever the cable was shortened may now be an  issue my question now is:  When did you last put a new battery in the  pen?

... Just after reading your suggestion that I do so. ^^;

It doesn't seem to have helped, however.  (It might be worth noting that I believe that the new battery is a rechargeable battery, and thus presumably has a lower voltage than a standard battery of its type.  Unfortunately, I don't think that I have any non-rechargeable batteries of this size to hand.)

>  Of course a secondary question is did anything we have done so far actually help?  Ouch.
Well, at the very least I've learned a bit more about Ubuntu and the various files to be found within it. ^^;

I do apologise for not having thought to test it under Windows first - that might have considerably shortened this process. :/

> I think you are talking about an old issue when the WizardPen driver was  the X driver for those tablets.  The WizardPen driver couldn't handle  the mousue node(s).  And that was back when the xorg.conf.d .conf files  were new.  It wasn't clear that:
```
Option "Ignore" "on"
```was what you were suppose to use in those situations so DoctorMO invented the:
```
Driver ""
```line as a substitute.  But it worked and does the same thing.
Aah, fair enough, and thank you for the explanation.

---

### Post by Favux on 2012-07-18
It could be the battery.  It might be the pen tip.  It might be the pen (the circuit board in it) is shot.

I know at least some models have a little screw on the circuit board, behind the battery I guess, that you can adjust for proximity sensitivity.  But I don't think what you are describing relates to that.  Other than the LED lighting up which sounded more like a weak battery.

---

### Post by ArsThaumaturgis on 2012-07-18
Hmm...  Fair enough, and thank you again for the aid.  I think that I'll look into at least some of those (the pen tip could really use replacing anyway, I think), but don't know when that might be.  For now this thread has run its course, I think, unless someone else wants to use it.

---

