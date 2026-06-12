---
title: "almost got a wacom bamboo touch working, need a little more help"
date: 2011-02-18
forum: Hardware
---

### Post by u-noob-tu on 2011-02-18
i have a wacom bamboo touch (model # CTT-460, touch only, no pen), and i installed the xf86-input-wacom driver and all the other necessary components and it is working. well, not completely. It recognizes the touch of my finger and the mouse moves appropriately, but i can't do any gestures like two finger tap or two finger swipes. the mouse just jumps wildly when i try. the buttons work, though, but id like to use the gestures (thats what it was intended to be used for). i havent been able to find a way to configure gesture support in linux (at least for my model). any help?

---

### Post by SnickerSnack on 2011-02-18
Favux has a few guides on getting tablets working.  You should search for them.  If you can't find one that covers what you need, then you might send him a pm.  Maybe he has some ideas on it that haven't been put into guide form yet.

---

### Post by Favux on 2011-02-19
Hi u-noob-tu,

I need a little more detail.  Did you install a wacom.ko (the usb kernel driver/module)?  If so from where?  Linuxwacom version #?  input-wacom version?

Which version of xf86-input-wacom did you install?

---

### Post by u-noob-tu on 2011-02-19
> **Favux said:**
> Hi u-noob-tu,

I need a little more detail.  Did you install a wacom.ko (the usb kernel driver/module)?  If so from where?  Linuxwacom version #?  input-wacom version?

Which version of xf86-input-wacom did you install?

i followed the steps here: [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562). steps 1 and 2 went through without a hitch, and the tablet responds to touch decently, but no multitouch. i have the versions of linuxwacom and input wacom listed there in the guide. i think my problem may be that i need to configure the tablet, but using xorg.conf to do so scares the crap out of me. :(

---

### Post by Favux on 2011-02-19
I think it should be working.  So something may not be right with the install.  But first...

You don't need to use the xorg.conf.  That's what the xsetwacom script described in part IV. and attached to the bottom is for.  Since you don't have a stylus or eraser just remove those two sections.  The parameter names have changed a little, mainly for you Button1 becomes Button 1, etc.  See the link to the new parameter table in part II. or use 'xsetwacom list parameters' so see the new names.

---

### Post by u-noob-tu on 2011-02-19
im sorry, im being a little thick headed. what exactly am i editing in the xsetwacom script? from what i can see in the script, it looks alright. i wasnt able to find the link to the parameter table you mentioned.

---

### Post by Favux on 2011-02-19
You'd be removing the sections headed by:
```
## stylus = ID 9 = "Wacom BambooFun 2FG 4x5 Pen stylus"
```
and
```
## eraser = ID 8 = "Wacom BambooFun 2FG 4x5 Pen eraser"
xsetwacom set 8 Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 8 RawSample "2"  # default is 2, 0-100
#xsetwacom set 8 ClickForce "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 8 Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 8 PressureCurve "0 10 90 100"  # Bezier curve, default is 0,0,100,100
#xsetwacom set 8 Mode "Absolute"  # or "Relative" cursor movement
```
since the Bamboo Touch doesn't have them.

The lines you're interested in are probably:
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Touch "on"  # or "off"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Gesture "on"  # or "off"
```

For the new parameter names enter in a terminal:
```
xsetwacom list parameters
```
or go to [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)

---

### Post by u-noob-tu on 2011-02-19
okay, heres what i have in the script after editing. ```
## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch, and pad.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## touch = ID 11 = "Wacom BambooFun 2FG 4x5 Finger touch"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Touch "on"  # or "off"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Gesture "on"  # or "off"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 11 RawSample "2"  #  default is 2, 0-100
#xsetwacom set 11 ClickForce "27"  # default is 27, range is 0-2047
xsetwacom set 11 Threshold "27"  # default is 27, range is 0-2047
xsetwacom set 11 Mode "Relative"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 11 ZoomDistance "50"  # default is 50
xsetwacom set 11 ScrollDistance "20"  # default is 20
xsetwacom set 11 TapTime "250"  # 2FG R click, default is 250 ms

## pad = ID 10 = "Wacom BambooFun 2FG 4x5 Finger pad"
xsetwacom set 10 Button1 "key ctrl t"  # toggle touch script
xsetwacom set 10 Button2 "key backspace"
xsetwacom set 10 Button3 "3"  # right mouse click
xsetwacom set 10 Button4 "key alt left"  # Back a page in FireFox

## Developed with dr4ziw and iRi_E
``` you said something about changing "Button1" to "Button 1", right? if thats all i need to do, i then just make this script executable and add it to start up programs and then im good to go, correct?

---

### Post by Favux on 2011-02-19
Correct, as far as the script goes.  Button2 becomes Button 2 and so on.  So now you have a "text" file where you can adjust your settings.  Not as good as a gui but about the best we can do for now.

---

### Post by u-noob-tu on 2011-02-19
okay, i made the script executable and set it up to run at start and rebooted, but it made no difference. no multitouch, and something i didnt notice before is that a single tap does not get registered as a left click, it just does nothing. maybe i messed up the install somehow. should i redo it?

---

### Post by Favux on 2011-02-19
That could be.  Or maybe there's a bug in xf86-input-wacom 0.10.11 for Bamboo touches.  Or maybe the linuxwacom 0.8.8-11 wacom.ko doesn't work for Bamboo touches anymore with 0.10.11.

To many possibilities are starting to open up.  Let's try some simple diagnostics first before we do anything else.  Enter in a terminal:
```
xinput list
```
and post the output.  Follow that with:
```
xsetwacom list
```
and
```
lsmod | grep wacom
```
and also posts those results.

---

### Post by u-noob-tu on 2011-02-19
here are the results: ```
ryan@ryan-Studio-1737:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Pen eraser                 id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Pen stylus                 id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Finger pad                 id=18    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG Finger touch               id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]

ryan@ryan-Studio-1737:~$ xsetwacom list
Wacom Bamboo 2FG Pen eraser         id: 16    type: ERASER    
Wacom Bamboo 2FG Pen stylus         id: 17    type: STYLUS    
Wacom Bamboo 2FG Finger pad         id: 18    type: PAD       
Wacom Bamboo 2FG Finger touch       id: 19    type: TOUCH     

ryan@ryan-Studio-1737:~$ lsmod | grep wacom
wacom                  30513  0 

```

just a wild guess, but it looks like its not identifying my tablet model correctly. it doesnt have pen/eraser support.

---

### Post by Favux on 2011-02-19
Actually that all looks good.  It says you have a stylus/eraser when you don't right now, I think.

So the only question is is the wacom.ko the one you compiled?  Navigate to it (use the copy command to tell you where) and using a right click and Properties check that the date is the day you compiled it.

---

### Post by u-noob-tu on 2011-02-19
> **Favux said:**
> Actually that all looks good.  It says you have a stylus/eraser when you don't right now, I think.

So the only question is is the wacom.ko the one you compiled?  Navigate to it (use the copy command to tell you where) and using a right click and Properties check that the date is the day you compiled it.

it says it was compiled today. the path to it is /lib/modules/2.6.35-22-generic/kernel/drivers/input/tablet/, is that right?

---

### Post by Favux on 2011-02-19
Yep, that all looks good too.  The mystery deepens.

Let's check your kernel and might as well get Xorg too:
```
Xorg -version
```
We should check your Xorg.0.log too.  It's in /var/log.  It's kind of big so compress it by right clicking on it and choosing Create Archive and attach it to your next post with Manage Attachments below.

---

### Post by u-noob-tu on 2011-02-20
heres Xorg -version: ```
ryan@ryan-Studio-1737:~$ Xorg -version

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux ryan-Studio-1737 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=6731c64b-2b2b-4bfc-ad71-31f71f5a1a8a ro quiet splash
Build Date: 09 January 2011  12:14:58PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```

and xorg.0.log is attached. at the bottom there are a lot of references to wacom and the words "no such device".

---

### Post by Favux on 2011-02-20
The Xorg.0.log shows that touch and pad seem to be setting up correctly on device input event 15.  Then it tries to setup stylus/eraser on the spurious device input event 14.  When that fails, a bunch of "no such device", it tries to set up touch/pad on 14.  After more "no such device", it then unloads the wacom module (wacom.ko).  Which is a problem, it's removed your usb driver.

So let's see if blocking it from trying to use stylus/eraser is enough to fix it, or do we need to block event 14 too?

So first change the usb snippet in 50-wacom.conf to:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	MatchProduct "Wacom Bamboo 2FG Pen"
	Option "Ignore" "yes"
EndSection

```
Remember to back up your currently working 50-wacom.conf and be prepared to restore it from backup at the command line if we break X.

---

### Post by u-noob-tu on 2011-02-21
> **Favux said:**
> The Xorg.0.log shows that touch and pad seem to be setting up correctly on device input event 15.  Then it tries to setup stylus/eraser on the spurious device input event 14.  When that fails, a bunch of "no such device", it tries to set up touch/pad on 14.  After more "no such device", it then unloads the wacom module (wacom.ko).  Which is a problem, it's removed your usb driver.

So let's see if blocking it from trying to use stylus/eraser is enough to fix it, or do we need to block event 14 too?

So first change the usb snippet in 50-wacom.conf to:
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    MatchProduct "Wacom Bamboo 2FG Pen"
    Option "Ignore" "yes"
EndSection

```Remember to back up your currently working 50-wacom.conf and be prepared to restore it from backup at the command line if we break X.

adding those 2 lines broke the driver, i think. i plugged in the bamboo and it no longer responded to touch and the hardware buttons didnt work either. i think youre on the right track in that something isnt getting loaded correctly.

---

### Post by Favux on 2011-02-21
Alright, let's try going at it the other way.  Let's try not hotplugging, leave the tablet plugged in.  As long as the ID # for touch is 15 consistently on boot up (from Xorg.0.log) try:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event15"
	Driver "wacom"
EndSection
```
Use the event # for touch you see in the Xorg.0.log.  If that works then we could try matching Finger so you can hot plug.

If other drivers try to set up on Pen they may interfere.  Another thing you can monitor with Xorg.0.log.

---

### Post by u-noob-tu on 2011-02-22
okay, adding that to the 50-wacom.conf didnt do much, but i was able to get right clicking to sort of work. it only right clicked when i had one finger slightly above the other when doing a two finger tap, but it was difficult to do and single tapping is still not registering as a left click.

---

### Post by Favux on 2011-02-22
Actually I think you have normal function now.

For a left click you have to double click one finger and that sends a left click.  Chris has submitted a patch to change that to a single tap but it hasn't been committed yet.  Currently it's sort of a single tap/click drag.

For right click one finger is down then bring down the second finger and that will bring up the right click menu.

If that's what you're seeing then we need to try to fix up the match so you can hot plug.

---

