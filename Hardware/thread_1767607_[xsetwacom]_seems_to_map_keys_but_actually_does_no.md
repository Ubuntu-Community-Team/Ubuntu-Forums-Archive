---
title: "[xsetwacom] seems to map keys but actually does nothing"
date: 2011-05-25
forum: Hardware
---

### Post by -Zeus- on 2011-05-25
Running 11.04 with an Intuos4 medium.

This used to work in 10.10 and previous.  When I run that command, it works fine, however, it actually does nothing.  When I try to use the button, it still has the same action as before (moves cursor to top left of screen).  I also tried using 'core key x' with the same results.

```
$ xsetwacom set 'Wacom Intuos4 6x9 pad' Button2 'key x'
$ xsetwacom get 'Wacom Intuos4 6x9 pad' Button2
2
```

```
KeyPress event, serial 36, synthetic NO, window 0x5000001,
    root 0x15a, subw 0x5000002, time 1154222, (38,27), root:(1427,74),
    state 0x10, keycode 120 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


However, this works (changes the setting to a different number), but the button function is exactly the same.

```
$ xsetwacom set 'Wacom Intuos4 6x9 pad' Button2 '3'
$ xsetwacom get 'Wacom Intuos4 6x9 pad' Button2
3
```


If anyone has ideas, I would greatly appreciate it.

---

### Post by Favux on 2011-05-26
Hi -Zeus-,

The parameter has changed.  There is now suppose to be a space between the button and the button's number, so:
```
xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 "key x"

```

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> Hi -Zeus-,

The parameter has changed.  There is now suppose to be a space between the button and the button's number, so:
```
xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 "key x"

```

Thanks for the reply.

```
matthew@POGO:~$ xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 "key x"
Unknown parameter name 'Button'.
matthew@POGO:~$ xsetwacom set "Wacom Intuos4 6x9 pad" "Button 2" "key x"
Unknown parameter name 'Button 2'.
```

Am I doing something wrong?  Perhaps I should try a newer version?

EDIT: Ok, so version 0.11.0 allows me to map some buttons, but buttons numbered 5 through 9 don't seem to do anything (they used to be the bottom four buttons on the tablet).  the top four work fine.  Also, for all the buttons, even when I map a keystroke, the cursor still jumps to the top-left corner of the screen when I press them (in addition to the key being pressed)

---

### Post by Favux on 2011-05-26
That is curious.  With Natty the default xf86-input-wacom should be 0.10.11.  Check in Synaptic Package Manager or Software Center for your version.  Or look in Xorg.0.log in /var/log.  Or run:
```
xsetwacom -V
```

---

### Post by Favux on 2011-05-26
Well the kernel defaults may have changed.  There was a 4 button offset because 4,5,6, and 7 were reserved for scroll.  So Button 4 was Button 8, etc.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Pad_Physical_Button_to_X_Button_Transpositions](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Pad_Physical_Button_to_X_Button_Transpositions)

The cursor jumping thing may be a pad bug we seem to be seeing in Natty.  I thought it was just the Graphires, but maybe not.  It's not clear if it is a Natty or a Wacom bug.  But a Cintiq switched to Debian testing (Wheezy) and said the button freezes and touchstrip segmentation faults went away.  Just got some debug info. from a Graphire.  I was hoping for some more on the Launchpad bug and then submit it to linuxwacom-discuss and see if anyone can figure out what's wrong.  I'm not seeing this on my BambooPT.

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> That is curious.  With Natty the default xf86-input-wacom should be 0.10.11.  Check in Synaptic Package Manager or Software Center for your version.  Or look in Xorg.0.log in /var/log.  Or run:
```
xsetwacom -V
```

```
matthew@POGO:~$ xsetwacom -V
0.11.0
```

I manually compiled xsetwacom, I don't think it's available for install in natty.

I was able to get all the buttons working.  The radial was button 1, the top four buttons were 2,3,8,9, the bottom four were 10-13.

Still having the issue with the cursor snapping to (0,0) when I press a button.

---

### Post by Favux on 2011-05-26
Very interesting.  Could you describe how you compiled xsetwacom please?  Other folks with Graphires are having problems with button freezes or even segmentation faults in Natty.  I'm wondering if it isn't related.  So detail would be appreciated.
> Still having the issue with the cursor snapping to (0,0) when I press a button. 
That may actually indicate the presumed Natty bug that is causing the problems.  Do you see anything in your Xorg.0.log when the cursor jumps to zero?  Would you be interested in producing a debug log so we might spot what's causing the jump, i.e. what's telling the pointer that it's coordinates are suddenly 0,0?  I don't know how much luck we'd have with that if it's actually an Xinput or Xserver bug Ubuntu has introduced in Natty and not something internal to the Wacom X driver.

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> Very interesting.  Could you describe how you compiled xsetwacom please?

I compiled x86 with git per [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

In terms of logging, tail -f /var/log/Xorg.0.log doesn't return anything when pressing the buttons.  xev shows the keypress but doesn't seem to show the mouse move (although it does display the changing window focus).

---

### Post by Favux on 2011-05-26
If you want to, we could see if we can get a trace of the error in the Xorg logs by adding debug statements to the 50-wacom.conf usb snippet. Add:
```
Option "CommonDBG" "12"
Option "DebugLevel" "12"
```
under the Driver "wacom" line. We may need to set up a dependent device snippet for "pad" and use DebugLevel in it. But let's try this first.  Warning, this will fill up Xorg.0.log with a lot of stuff.

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> ```
Option "CommonDBG" "12"
Option "DebugLevel" "12"
```

```
tail -f -n 0 /var/log/Xorg.0.log > /tmp/wacom
```

I just pressed one button, which was mapped to the x key (which did appear onscreen, and my mouse did snap as before).

```
[ 69345.780] (II) Wacom Intuos4 6x9 pad (10:wcmReady): 1 numbers of data
[ 69345.781] (II) /dev/input/event3 (10:wcmReadPacket): fd=28
[ 69345.781] (II) /dev/input/event3 (1:wcmReadPacket): pos=0 remaining=256
[ 69345.781] (II) /dev/input/event3 (10:wcmReadPacket): buffer has 80 bytes
[ 69345.781] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.781] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.781] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.781] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.781] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.781] (II) /dev/input/event3 (6:usbDispatchEvents): 5 events received
[ 69345.781] (II) /dev/input/event3 (11:usbDispatchEvents): event[0]->type=1 code=263 value=1
[ 69345.781] (II) /dev/input/event3 (11:usbDispatchEvents): event[1]->type=1 code=325 value=1
[ 69345.781] (II) /dev/input/event3 (6:usbParseKeyEvent): USB Pad detected 145 (value=1)
[ 69345.781] (II) /dev/input/event3 (11:usbDispatchEvents): event[2]->type=3 code=40 value=15
[ 69345.781] (II) /dev/input/event3 (11:usbDispatchEvents): event[3]->type=4 code=0 value=-1
[ 69345.781] (II) /dev/input/event3 (11:usbDispatchEvents): event[4]->type=0 code=0 value=0
[ 69345.781] (II) /dev/input/event3 (10:wcmEvent): channel = 1
[ 69345.781] (II) /dev/input/event3 (10:wcmEvent): c=1 i=15 t=16 s=4294967295 x=0 y=0 b=128 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 px=1 st=0 cs=0 
[ 69345.781] (II) /dev/input/event3 (10:wcmCheckSuppress): level = 2 return value = 8
[ 69345.781] (II) /dev/input/event3 (10:commonDispatchDevice): device type = 16
[ 69345.781] (II) /dev/input/event3 (11:commonDispatchDevice): tool id=16 for Wacom Intuos4 6x9 pad
[ 69345.781] (II) Wacom Intuos4 6x9 pad (7:wcmSendEvents): [PAD] o_prox=false x=0 y=0 z=0 b=true b=128 tx=0 ty=0 wl=0 rot=25 th=0
[ 69345.781] (II) Wacom Intuos4 6x9 pad (10:wcmRotateAndScaleCoordinates): rotate/scaled to 0/0
[ 69345.781] (II) Wacom Intuos4 6x9 pad (6:wcmSendEvents): abs prox=1	x=0	y=0	z=0	v3=0	v4=0	v5=0	id=15	serial=4294967295	button=true	buttons=128
[ 69345.781] (II) Wacom Intuos4 6x9 pad (6:wcmSendButtons): buttons=128
[ 69345.781] (II) Wacom Intuos4 6x9 pad (4:sendAButton): TPCButton(off) button=7 state=128 mapped_button=12, coreEvent=no 
[ 69345.781] (II) Wacom Intuos4 6x9 pad (10:wcmReady): 0 numbers of data
[ 69345.781] (II) Wacom Intuos4 6x9 pad (10:wcmDevReadInput): Read (1)
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmGetProperty): 
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmGetProperty): Update to serial: -1
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.782] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.957] (II) Wacom Intuos4 6x9 pad (10:wcmReady): 1 numbers of data
[ 69345.957] (II) /dev/input/event3 (10:wcmReadPacket): fd=28
[ 69345.957] (II) /dev/input/event3 (1:wcmReadPacket): pos=0 remaining=256
[ 69345.957] (II) /dev/input/event3 (10:wcmReadPacket): buffer has 80 bytes
[ 69345.957] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.957] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.957] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.957] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.957] (II) /dev/input/event3 (10:usbParseEvent): 
[ 69345.957] (II) /dev/input/event3 (6:usbDispatchEvents): 5 events received
[ 69345.957] (II) /dev/input/event3 (11:usbDispatchEvents): event[0]->type=1 code=263 value=0
[ 69345.957] (II) /dev/input/event3 (11:usbDispatchEvents): event[1]->type=1 code=325 value=0
[ 69345.957] (II) /dev/input/event3 (6:usbParseKeyEvent): USB Pad detected 145 (value=0)
[ 69345.957] (II) /dev/input/event3 (11:usbDispatchEvents): event[2]->type=3 code=40 value=0
[ 69345.957] (II) /dev/input/event3 (11:usbDispatchEvents): event[3]->type=4 code=0 value=-1
[ 69345.957] (II) /dev/input/event3 (11:usbDispatchEvents): event[4]->type=0 code=0 value=0
[ 69345.957] (II) /dev/input/event3 (10:wcmEvent): channel = 1
[ 69345.957] (II) /dev/input/event3 (10:wcmEvent): c=1 i=15 t=16 s=4294967295 x=0 y=0 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 px=0 st=0 cs=1 
[ 69345.957] (II) /dev/input/event3 (10:wcmCheckSuppress): level = 2 return value = 8
[ 69345.957] (II) /dev/input/event3 (10:commonDispatchDevice): device type = 16
[ 69345.957] (II) /dev/input/event3 (11:commonDispatchDevice): tool id=16 for Wacom Intuos4 6x9 pad
[ 69345.957] (II) Wacom Intuos4 6x9 pad (7:wcmSendEvents): [PAD] o_prox=true x=0 y=0 z=0 b=false b=0 tx=0 ty=0 wl=0 rot=25 th=0
[ 69345.957] (II) Wacom Intuos4 6x9 pad (6:wcmSendEvents): abs prox=0	x=0	y=0	z=0	v3=0	v4=0	v5=0	id=15	serial=4294967295	button=false	buttons=0
[ 69345.957] (II) Wacom Intuos4 6x9 pad (6:wcmSendButtons): buttons=0
[ 69345.957] (II) Wacom Intuos4 6x9 pad (4:sendAButton): TPCButton(off) button=7 state=0 mapped_button=12, coreEvent=no 
[ 69345.957] (II) Wacom Intuos4 6x9 pad (10:wcmReady): 0 numbers of data
[ 69345.957] (II) Wacom Intuos4 6x9 pad (10:wcmDevReadInput): Read (1)
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmGetProperty): 
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmGetProperty): Update to serial: -1
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
[ 69345.958] (II) Wacom Intuos4 6x9 pad (10:wcmSetProperty): 
```

---

### Post by Favux on 2011-05-26
Thanks!  Nothing jumps out at me as involving the Wacom X driver.  Since you're seeing 6:usbParseKeyEvent and the Pad is detected along with with the button event and you're not seeing a button freeze the jump is probably unrelated to the Graphire problem.  Of course I could just be missing it.

So I have no explanation.  Is the pointer drawing lines in Gimp or whatever when it jumps?  Are you changing the Mode of the pad somewhere?

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> Thanks!  Nothing jumps out at me as involving the Wacom X driver.  Since you're seeing 6:usbParseKeyEvent and the Pad is detected along with with the button event and you're not seeing a button freeze the jump is probably unrelated to the Graphire problem.  Of course I could just be missing it.

So I have no explanation.  Is the pointer drawing lines in Gimp or whatever when it jumps?  Are you changing the Mode of the pad somewhere?

If I am drawing a line in gimp while I press a button the line goes straight off the canvas (to the upper left corner)... I only have one mode.  I'm confused as to what would start causing this now.  I wonder if it has anything to do with Unity?

---

### Post by Favux on 2011-05-26
The driver default Mode for pad, correct?

That's what I am thinking.  Have you tried to see if Classic mode fixes it?

---

### Post by -Zeus- on 2011-05-26
> **Favux said:**
> The driver default Mode for pad, correct?

That's what I am thinking.  Have you tried to see if Classic mode fixes it?

Oh sorry.  I'm unsure how to change that - can you give me the short version?

---

### Post by Favux on 2011-05-26
Sure, I'm not surprised you missed it.  When you restart and the log in screen comes up look at the bottom.  Along with the language and country selector there's one called Ubuntu.  Click on the double arrow selector thingy and up will pop your choices.  So you'll probably want to try Classic and Classic (No effects).

---

### Post by -Zeus- on 2011-05-28
> **Favux said:**
> Sure, I'm not surprised you missed it.  When you restart and the log in screen comes up look at the bottom.  Along with the language and country selector there's one called Ubuntu.  Click on the double arrow selector thingy and up will pop your choices.  So you'll probably want to try Classic and Classic (No effects).

Oh ok I thought you were talking about driver modes.  I tried both of those and the same happens.  I guess I can work around it for now, since when I actually have the pen on the pad it snaps right back to its original position after I press the button.  It's just a bit annoying.

Any more ideas?

---

### Post by Favux on 2011-05-28
OK, you've established that it likely isn't Unity causing the problem.  So that's good to know.

That makes it sound more like a driver problem.  Right now with Graphire tablets we're seeing a pad button freeze after the stylus is used.  That is looking like it is do to a misalignment of the kernel driver with the xf86-input-wacom driver.  We're trying to get someone with a Graphire to patch their kernel and test some minor changes.

I'm sort of wondering if you are seeing something similar?

We might want to look at more of the debug Xorg.0.log and see if anything turns up or maybe make some debugs tracing the stylus and pad too.

You should also consider posting on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)  and see if you can get some help.

---

### Post by Favux on 2011-06-05
Hi -Zeus-,

Sanette is seeing the same cursor jump with button press on his Intuous4:  [http://ubuntuforums.org/showthread.php?t=1380744&page=20](http://ubuntuforums.org/showthread.php?t=1380744&page=20)

---

