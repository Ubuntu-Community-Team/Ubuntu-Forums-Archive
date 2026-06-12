---
title: "Trying to set up a Wacom Pen &amp; Touch with Lucid"
date: 2010-09-17
forum: Hardware
---

### Post by tosca30 on 2010-09-17
Up to this morning, I was using an old Wacom tablet (pen only) that worked like a charm.

Now I'm trying to set up a new Bamboo Pen & Touch according to this tutorial: [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

I managed to complete steps I, II and III (by the way, I don't see any option when using "man wacom" in a terminal), but am stucked after that, and don't understand what has to be done.

The pen appears to work quite properly, but the touch doesn't seem to respond like it should. In addition, I need to set up the tablet as left-handed, and would like to be able to customize the express keys.

Can somebody help me to achieve this?

I'm using a Toshiba Satellite P300 laptop with Lucid (kernel 2.6.32.24).

Thanks for helping.

---

### Post by Favux on 2010-09-17
Hi tosca30,

Welcome to Ubuntu forums!

What did you do in step III.?  Usually you don't have to do anything as the default 10-wacom.conf works for most.

---

### Post by tosca30 on 2010-09-17
> **Favux said:**
> Hi tosca30,

Welcome to Ubuntu forums!
Thanks, I've already used the French forums for the past year, but I thought this one would be better for such a specific topic.

> **Favux said:**
> What did you do in step III.?  Usually you don't have to do anything as the default 10-wacom.conf works for most.
I'm afraid I didn't realise it was optional ...

I didn't understand the **a)** option, so I went for **b)i)** (not sure that's a good reason!) and add lines from the *test3* file (only those related to the tablet), then **b)ii)**.

---

### Post by Favux on 2010-09-17
The xorg.conf is fine but you lose hot plugging.  With a laptop you probably want that.  It sounds like you didn't do anything to your 10-wacom.conf.  If using the xorg.conf you would probably remove it.

So just comment out (#) the Wacom sections in the xorg.conf, and the Wacom lines in "ServerLayout" and then reboot.  That should restore you to a default configuration.  Then you want to install the xsetwacom script.  If touch is still wonky we should be able to fix that.

---

### Post by tosca30 on 2010-09-17
> **Favux said:**
> 
So just comment out (#) the Wacom sections in the xorg.conf, and the Wacom lines in "ServerLayout" and then reboot.
Done.
> **Favux said:**
> Then you want to install the xsetwacom script.
That was part IV of the tutorial? Done too.
> **Favux said:**
> If touch is still wonky we should be able to fix that.
I'm afraid I can't see much difference.

---

### Post by Favux on 2010-09-17
Alright, up near the top is some blue lettering directing you to the touch fix in post #110 or down in Troubleshooting at the bottom of the HOW TO.  You'll need to change a line in the unpacked xf86-input-wacom source code and recompile it (II.).  Just remember to do the 'make clean' before doing the autgen.sh.

---

### Post by tosca30 on 2010-09-17
That's much better: the touch seems to work, with zoom in/out, though I didn't have success with rotate yet. But it might need some practice.

However, the left-handed option still doesn't work, although I have put all the 'rotate HALF' options in the .xsetwacom.sh

And about the express keys, and the different touches, is it possible to customize their settings?

---

### Post by Favux on 2010-09-17
Hi tosca30,

Good, gestures are working.

Show me the xsetwacom commands you are using for rotation.

Yes, the .xsetwacom.sh shows you how to customize the settings.  What do you want to do?

Probably a good idea to post your 'xinput --list'.

---

### Post by tosca30 on 2010-09-17
> **Favux said:**
> 

Show me the xsetwacom commands you are using for rotation.
I added the 'rotate HALF' commands to the .xsetwacom.sh, so nom it is:
```
## For xorg.conf or Karmic & Jaunty if using the modified .fdi's.

## stylus
xsetwacom set stylus Suppress "2"  # data trimmed, 0-100
xsetwacom set stylus RawSample "20"  #default is 4
xsetwacom set stylus ClickForce "6"  # default is 4
xsetwacom set stylus PressCurve "5 10 90 95"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Mode "Absolute"  # or Relative
xsetwacom set stylus Button1 "1"  # left mouse click
xsetwacom set stylus Button2 "3"  # right mouse click
xsetwacom set stylus Button3 "2"  # middle mouse click
xsetwacom set stylus rotate HALF 


## eraser
xsetwacom set eraser Suppress "2"  # data trimmed, 0-100
xsetwacom set eraser RawSample "20"  #default is 4
xsetwacom set eraser ClickForce "6"  # default is 4
xsetwacom set eraser PressCurve "0 10 90 100"
xsetwacom set eraser Mode "Absolute"  # or Relative
xsetwacom set eraser Button1 "1"
xsetwacom set eraser rotate HALF


## touch
xsetwacom set touch Touch "on"
xsetwacom set touch Gesture "on"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set touch ZoomDistance "50"  # default is 50
xsetwacom set touch ScrollDistance "20"  # default is 20
xsetwacom set touch TapTime "250"  # 2FG R click, default is 250 ms
xsetwacom set touch rotate HALF

## pad
xsetwacom set pad Button1 "key ctrl t"  # toggle touch script
xsetwacom set pad Button2 "key backspace"
xsetwacom set pad Button3 "3"  # right mouse click
xsetwacom set pad Button4 "key alt left"  # Back a page in FireFox

```> **Favux said:**
> Yes, the .xsetwacom.sh shows you how to customize the settings.  What do you want to do?
I'm not sure what I will want to change eventually.
At first, I would like to know what each touch is supposed to do. The only documentation I have is the CD provided with the tablet, and it cannot be run with Linux (it contains Windows .exe programs).


> **Favux said:**
> Probably a good idea to post your 'xinput --list'.
Here it is:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser          id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus          id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad          id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger touch        id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=16    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
```

---

### Post by Favux on 2010-09-17
Alright, the xinput list tells you what your "Device names" are.  Since you're no longer using xorg.conf they are no longer sylus, eraser, etc.  So, for example:
```
xsetwacom set stylus Suppress "2"  # data trimmed, 0-100

```
becomes
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Suppress "2"  # data trimmed, 0-100

```
and
```
xsetwacom set stylus rotate HALF 

```
becomes
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" rotate HALF 

```
And similarly for eraser, touch, and pad.  You can also use the ID # but since that can change with hot plugging the "Device name" is better.

To experiment with changing the pad (tablet buttons) you can just enter a xsetwacom command in a terminal and hit enter.  The change will be applied immediately.  With the latest versions of xf86-input-wacom entering 'man xsetwacom' into a terminal should give you the manual.  Also see:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by tosca30 on 2010-09-18
> **Favux said:**
> Alright, the xinput list tells you what your "Device names" are. ...And similarly for eraser, touch, and pad. []("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")
Here is the new *.xsetwacom.sh* :
```
## For xorg.conf or Karmic & Jaunty if using the modified .fdi's.

## stylus
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" RawSample "20"  #default is 4
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" ClickForce "6"  # default is 4
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" PressCurve "5 10 90 95"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" TPCButton "on"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Mode "Absolute"  # or Relative
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Button1 "1"  # left mouse click
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Button2 "3"  # right mouse click
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" Button3 "2"  # middle mouse click
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" rotate HALF 


## eraser
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" RawSample "20"  #default is 4
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" ClickForce "6"  # default is 4
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" PressCurve "0 10 90 100"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" Mode "Absolute"  # or Relative
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" Button1 "1"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen eraser" rotate HALF


## touch
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" Touch "on"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" Gesture "on"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" ZoomDistance "50"  # default is 50
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" ScrollDistance "20"  # default is 20
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" TapTime "250"  # 2FG R click, default is 250 ms
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen touch" rotate HALF

## pad
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen pad" Button1 "key ctrl t"  # toggle touch script
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen pad" Button2 "key backspace"
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen pad" Button3 "3"  # right mouse click
xsetwacom set "Wacom BambooFun 2FG 4x5 Pen pad" Button4 "key alt left"  # Back a page in FireFox

```
But the tablet is still right-handed after reboot.

---

### Post by Favux on 2010-09-18
What video chipset do you have?
```
lspci | grep VGA
```
And which video drivers for it?

---

### Post by tosca30 on 2010-09-18
```
lspci | grep VGA
```
returns:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```> **Favux said:**
> And which video drivers for it?
Euh ... and how am I to know that?

---

### Post by Favux on 2010-09-18
Well if you used Hardware Drivers in System > Administration to activate the ATI proprietary drivers it's the proprietary drivers.  If not then it's the opensource radeon driver (most likely).

---

### Post by tosca30 on 2010-09-18
> **Favux said:**
> Well if you used Hardware Drivers in System > Administration to activate the ATI proprietary drivers it's the proprietary drivers.
I don't remember having done that ... but I might have forgotten what has been done (and not understood) a year ago.

---

### Post by Favux on 2010-09-18
Well check in Hardware Drivers and see if you activated it.  If so to get rotation you might have to run the command:
```
sudo aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
```
That's from Appendix 1 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") which links to the ATI wiki.

---

### Post by tosca30 on 2010-09-18
Just tried Système -> Administration -> Pilote de périphériques and it returns "Des pilotes propriétaires sont actuellement utilisés ...", then "Pilote propriétaire ATI/AMD pour carte graphique".

Edit: I dit the *aticonfig* command and rebooted, but no change.

---

### Post by Favux on 2010-09-18
See if changing 'rotate' in the commands to 'Rotate' makes a difference.  Also try putting HALF into quotes to see if that helps, "HALF".

---

### Post by Favux on 2010-09-18
You could also comment out the xsetwacom Rotate commands and try adding to the usb snippet in 10-wacom.conf:
```
    Option "Rotate" "HALF"
```
as in
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Rotate" "HALF"
EndSection
```
Use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```

---

### Post by tosca30 on 2010-09-18
> **Favux said:**
> You could also comment out the xsetwacom Rotate commands and try adding to the usb snippet in 10-wacom.conf:
...]
THAT DID IT!
Thanks a lot for your patience and helpfulness.

For now, I will try to get use to the touch functionalities, that are completely new for me.
I might have a few other questions when I need to tune it up in the near future.;)

):P

---

### Post by Favux on 2010-09-18
Hi tosca30,

Nice work!  :)  You're welcome.

I'm starting to wonder if the xsetwacom Rotate command is broken.  Some Lenova X61 tablet pc users are experiencing similar problems.

---

### Post by tosca30 on 2010-09-18
> **Favux said:**
> 

I'm starting to wonder if the xsetwacom Rotate command is broken.  Some Lenova X61 tablet pc users are experiencing similar problems.

I wouldn't know ... but if you think I can provide any more information, feel free to ask.
:)

---

