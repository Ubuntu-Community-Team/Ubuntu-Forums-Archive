---
title: "Acer 5542 (touchpad &amp; microphone)"
date: 2010-02-16
forum: Hardware
---

### Post by Gennadich on 2010-02-16
Hello. I have Acer 5542 laptop and Ubuntu 9.10 and this is my story)

pre: on this laptop touchpad on/off button is separated (not Fn+F7) and situated near touchpad.

Q:
When I start working with Ubuntu, touchpad is working (touchpad on/off button is in Off position (no light) ), but when I press touchpad on/off button, touchpad stops working and on/off button pressing gives no result except highlight.
Also my microphone doesn't work.

Can anybody help?

---

### Post by pi/roman on 2010-02-16
You could try to identify what is being changed by setting up monitors. Open up 3 terminal windows.
In the first one put a udev monitor.
```
udevadm monitor
```In the second put lshal monitor:
```
lshal -m
```In the third put an xinput monitor, first check the name of your touchpad:
```
xinput list --short
```then monitor the touchpad device using the name you found:
```
xinput watch-props "SynPS/2 Synaptics TouchPad"
```Then press the power button and see if anything comes up in the monitors.

---

### Post by Gennadich on 2010-02-17
first window: no changes

second window: 
09:11:42.500: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = f22 (I press the on/off touchpad button and it highlights)
09:11:48.614: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = f22 (I press it again and indicator is off)
nothing more about touchpad in this terminal

third window:

"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]

this is what I get at start

```

    Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (116):    1
    Synaptics Edges (260):    1752, 5192, 1620, 4236
    Synaptics Finger (261):    24, 29, 255
    Synaptics Tap Time (262):    180
    Synaptics Tap Move (263):    221
    Synaptics Tap Durations (264):    180, 180, 100
    Synaptics Tap FastTap (265):    0
    Synaptics Middle Button Timeout (266):    75
    Synaptics Two-Finger Pressure (267):    280
    Synaptics Two-Finger Width (268):    7
    Synaptics Scrolling Distance (269):    100, 100
    Synaptics Edge Scrolling (270):    0, 0, 0
    Synaptics Two-Finger Scrolling (271):    1, 1
    Synaptics Move Speed (272):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (273):    29, 159
    Synaptics Edge Motion Speed (274):    1, 401
    Synaptics Edge Motion Always (275):    0
    Synaptics Button Scrolling (276):    1, 1
    Synaptics Button Scrolling Repeat (277):    1, 1
    Synaptics Button Scrolling Time (278):    100
    Synaptics Off (279):    0
    Synaptics Guestmouse Off (280):    0
    Synaptics Locked Drags (281):    0
    Synaptics Locked Drags Timeout (282):    5000
    Synaptics Tap Action (283):    0, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (284):    1, 1, 1
    Synaptics Circular Scrolling (285):    0
    Synaptics Circular Scrolling Distance (286):    0.100000
    Synaptics Circular Scrolling Trigger (287):    0
    Synaptics Circular Pad (288):    0
    Synaptics Palm Detection (289):    0
    Synaptics Palm Dimensions (290):    10, 199
    Synaptics Coasting Speed (291):    0.000000
    Synaptics Pressure Motion (292):    29, 159
    Synaptics Pressure Motion Factor (293):    1.000000, 1.000000
    Synaptics Grab Event Device (294):    1
    Synaptics Area (295):    0, 0, 0, 0
    Synaptics Capabilities (296):    1, 1, 1, 0, 0
    Synaptics Jumpy Cursor Threshold (297):    0
```and this I get every time I start and stop typing (In laptop manual they said that touchpad will be blocked when typing and it seems that this is it.)

```

Property 'Synaptics Off' changed.
    Synaptics Off (279):    1
Property 'Synaptics Off' changed.
    Synaptics Off (279):    0
```So, Touchpad just stop working 

This is log of condition of touchpad when it doesn't work

```
    
    Device Enabled (116):    1
    Synaptics Edges (260):    1752, 5192, 1620, 4236
    Synaptics Finger (261):    24, 29, 255
    Synaptics Tap Time (262):    180
    Synaptics Tap Move (263):    221
    Synaptics Tap Durations (264):    180, 180, 100
    Synaptics Tap FastTap (265):    0
    Synaptics Middle Button Timeout (266):    75
    Synaptics Two-Finger Pressure (267):    280
    Synaptics Two-Finger Width (268):    7
    Synaptics Scrolling Distance (269):    100, 100
    Synaptics Edge Scrolling (270):    0, 0, 0
    Synaptics Two-Finger Scrolling (271):    1, 1
    Synaptics Move Speed (272):    0.400000, 0.700000, 0.009952, 40.000000
    Synaptics Edge Motion Pressure (273):    29, 159
    Synaptics Edge Motion Speed (274):    1, 401
    Synaptics Edge Motion Always (275):    0
    Synaptics Button Scrolling (276):    1, 1
    Synaptics Button Scrolling Repeat (277):    1, 1
    Synaptics Button Scrolling Time (278):    100
    Synaptics Off (279):    0
    Synaptics Guestmouse Off (280):    0
    Synaptics Locked Drags (281):    0
    Synaptics Locked Drags Timeout (282):    5000
    Synaptics Tap Action (283):    0, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (284):    1, 1, 1
    Synaptics Circular Scrolling (285):    0
    Synaptics Circular Scrolling Distance (286):    0.100000
    Synaptics Circular Scrolling Trigger (287):    0
    Synaptics Circular Pad (288):    0
    Synaptics Palm Detection (289):    0
    Synaptics Palm Dimensions (290):    10, 199
    Synaptics Coasting Speed (291):    0.000000
    Synaptics Pressure Motion (292):    29, 159
    Synaptics Pressure Motion Factor (293):    1.000000, 1.000000
    Synaptics Grab Event Device (294):    1
    Synaptics Area (295):    0, 0, 0, 0
    Synaptics Capabilities (296):    1, 1, 1, 0, 0
    Synaptics Jumpy Cursor Threshold (297):    0

```It' tha same that I have when it works. By the way, even when touchpad was "ON" scroll doesn't work at all.


ADDED:
I tried to search in internet by keywords Synaptics. I even install GSynaptics but it still doesn't work.

---

### Post by Gennadich on 2010-02-17
Microphone works!!! I searched the internet and found a statement that the microphone is muted by default. For the sake of interest useful in setting and indeed my microphone was muted. )))

---

### Post by pi/roman on 2010-02-17
Everything looks normal from all the outputs. The only output that reported pertinent  information was
> 09:11:42.500: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = f22 (I press the on/off touchpad button and it highlights)
09:11:48.614: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = f22 (I press it again and indicator is off)Since it doesn't appear to be doing anything strange on the face, although we know it is doing something strange, the best option may be to disable that key.
So first you need to get the keycode for it. Try
```
xmodmap -pke | grep f22
```If the keycode shows up for it good, if not try to find it using another monitor by typing "xev" and pressing enter. Pressing the key should bring up a keypress and keyrelease output then you can use alt/f4 to close the xev window without putting out to much extra output.
So now if you have the keycode, I'm not sure what it is yet but let's use a hypothetical keycode   955, you could disable keycode  955 by:
```
xmodmap -e "keycode 955 = "
```substituting the keycode you found.  Then if that works just add it to startup applications to disable it every time.

---

### Post by pi/roman on 2010-02-17
If you want to fix your scrolling action I have a guide here:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

You can just go to section 3 to find your horizedgescroll and vertedgescroll options then go to section 4b to make permanent adjustment to them through hal.  There are also methods in the addendum of the guide to toggle the touchpad on and off if you want another way to do that.

---

### Post by pi/roman on 2010-02-20
Did both solutions work?

---

### Post by Gennadich on 2010-02-23
not tested yet. As far as I do that, I leave a result report

---

### Post by Gennadich on 2010-02-24
> **pi/roman said:**
> Everything looks normal from all the outputs. The only output that reported pertinent  information was
............
Then if that works just add it to startup applications to disable it every time.

well.... here is my report
***xmodmap -pke | grep f22*** - nothing happened
***xev*** - 

```
KeyPress event, serial 36, synthetic NO, window 0x6400001,
    root 0x9d, subw 0x0, time 28633911, (269,50), root:(743,285),
    state 0x10, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XmbLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6400001,
    root 0x9d, subw 0x0, time 28633987, (269,50), root:(743,285),
    state 0x10, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x6400001,
    root 0x9d, subw 0x0, time 28634961, (269,50), root:(743,285),
    state 0x10, keycode 200 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x6400001,
    root 0x9d, subw 0x0, time 28634971, (269,50), root:(743,285),
    state 0x10, keycode 200 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```(I pressed "q" key one time - two actions for down and up and double press on touchpad button)

As far as I understand - my keycode - 200?
[I][B]
xmodmap -e "keycode 200 = "[/B][/I] - nothing happened again(

I didn't tested second solution, 'cause I can't make first works.((

---

### Post by pi/roman on 2010-02-24
Because of this output> keycode 200 (keysym 0x0, NoSymbol)it appears this key is already undefined so I am guessing that it is hardwired to the touchpad and therefore would be unable to be tweaked.
Two things to doublecheck would be if this key is already registered as a shortcut key by typing alt/f2:
```
gnome-keybinding-properties
```and looking for a touchpad shortcut.
Also, after rebooting to clear out the keymap adjustment, type in terminal:
```
xmodmap -pke | grep 200
```to doublecheck whether anything is registered to it.

---

### Post by Gennadich on 2010-02-25
I tried to find this option in shortcut keys, but it was ineffectively.
Then I tried to put an sound on/off function to this button. It worked. So, it seems I just need right command to add shortcut key for this button.

Also... 

If I press this button before starting the operating system, the button is highlighted, and after running OS, by it's pressing the touchpad does not turn off. And only when you press the button again, touchpad turns off.

---

### Post by pi/roman on 2010-02-25
> Then I tried to put an sound on/off function to this button. It worked. So, it seems I just need right command to add shortcut key for this button.You should be able to assign shortcuts to this key but that will not fix your problem because the key is hardwired to the touchpad through a switch that is bad.  You should contact Acer support by going to their website and following support links: [[COLOR=Blue]www.**acer**.com[/COLOR]]("http://www.acer.com").
Check with them whether it is possible to disable your touchpad toggle switch.

It may be necessary to send your laptop in to have it repaired. The instructions here should allow you to do that: [[COLOR=Blue]http://secure2.tx.acer.com/FixMyAcer3/FixMyAcer.aspx[/COLOR]]("http://secure2.tx.acer.com/FixMyAcer3/FixMyAcer.aspx")

---

### Post by Gennadich on 2010-02-25
Thanx, I think Thread may be closed

---

### Post by tb070 on 2010-11-29
I too got the Touchpad problem on my Acer: whenever turned it on/off with the hw button (hardware) next to the pad, Maverick did the opposite (showing in a pop-up).    

My solution was:

[LIST]
[*]So I logged out.
[*]Turned the touchpad OFF using hw button. (light on)
[*]Then logged in.
[*]Turned the touchpad ON using hw button next to touchpad. (light off)
[/LIST]
 ét voilà... hw and Maverick were in sync!  It's a wierd yet simple bug.  Hopes this helpes.

---

