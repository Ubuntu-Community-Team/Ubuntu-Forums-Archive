---
title: "Instantaneous touchpad 'tap' response"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by robin.com.au on 2007-02-19
UPDATE 27-02-07
Open /etc/X11/xorg.conf
Remove  [COLOR="Blue"]InputDevice "Synaptics Touchpad"[/COLOR] 
and tapping response will be INSTANTANEOUS and fault-tolerant, meaning that a 'click' will always be registered immediately no matter how soft or hard you do a tap, and it is almost impossible to accidentally click on something else while moving the touchpad around. But it sucks because you can't touch-scroll, multi-finger tap, drag and everything, except basic moving and tapping.

With [COLOR="Blue"]InputDevice "Synaptics Touchpad"[/COLOR], it's 'noticeably' slow to register a tap, and sometimes not register at all. Compare tapping on something and using the touchpad 'buttons' to left click. I think I found a solution but it's still not as perfect as without Synaptics.

Open /etc/X11/xorg.conf , find the following section and add the Coloured bits.
------------------------------------------
Identifier  "Synaptics Touchpad"
  Driver    "synaptics"
  Option    "SendCoreEvents"  "true"
  Option    "Device"    "/dev/psaux"register
  Option    "Protocol"    "auto-dev"
  Option    "HorizScrollDelta"  "0"
  [COLOR="Blue"]Option    "SingleTapTimeout"  "0"[/COLOR]
  [COLOR="Green"]Option       "FingerLow"     "60"#release when lower, default value is 25
  Option       "FingerHigh"    "60"#touch when higher, default value is 30[/COLOR]
  [COLOR="#0000ff"]Option    "ClickTime"     "0[/COLOR]"
 [COLOR="Orange"]Option      "FastTaps" "1"[/COLOR]
  Option    "SHMConfig"     "on" #added for changing these 'Options' on the fly without ctrl+alt+backspace all the time
EndSection
-------------------------------------------------

[COLOR="Blue"]Blue[/COLOR] are the additions which makes tapping pretty much 'instantaneous', as responsive as when you use the plastic touchpad 'buttons' instead.

But still it seems some of my taps do not register sometimes so:
[COLOR="Green"]Green[/COLOR] bits are added and seems to makes tapping more responsive for ME, but you need to experiment with the numbers. I do not understand how FingerHigh/Low work, it confused me. I thought bigger numbers mean more pressure, therefore tap harder, but it did just the opposite, it seems to register more softer taps and register taps better, but I DON'T KNOW. Someone do explain it to me.

[COLOR="Orange"]Orange[/COLOR] may make tap response better. Not too sure. Try it on and off and see if it makes any difference.

Open up a terminal and use 'synclient'. 
Type: [COLOR="#0000ff"]synclient -l[/COLOR]
And that lists all the 'Options' and its 'current' values.

You can change these 'Options' on the fly if you have SHMConfig on.
For example:
Type: [COLOR="#0000ff"]synclient SingleTapTimeout=0[/COLOR]
So you can do this instead of opening up xorg.conf and put in [COLOR="Blue"]Option  "SingleTapTimeout"  "0"[/COLOR] then ctrl+alt+bkspace

I avoided using apps like gsynaptics, ksynaptics, qsynaptics because I don't know which 'Options' those scrollbars and checkboxes change.

BUUUUUT another problem arises,  [COLOR="Red"]I cannot tap-drag[/COLOR], or double-tap-drag, because of [COLOR="Blue"]SingleTapTimeout[/COLOR].

I'm assuming [COLOR="Blue"]MaxDoubleTapTime[/COLOR] value must be equal or less than the value of [COLOR="Blue"]SingleTapTimeout[/COLOR] so that [COLOR="Blue"]MaxDoubleTapTime[/COLOR] has time to register before [COLOR="Blue"]SingleTap[/COLOR] TIMESOUT.

But since I told you guys to give [COLOR="Blue"]SingleTapTimeout[/COLOR] a value of '0', what is [COLOR="Blue"]MaxDoubleTapTime[/COLOR] to do?

Maybe play with those values and see if it works in your favour.

So it's either INSTANT tap response OR  tap-drag. Not both. bleh
Any ideas if I want both? Or do I need to continue posting to myself?

[COLOR="green"]--------Another update to myself---------[/COLOR]
Giving both [COLOR="Blue"]SingleTapTimeout[/COLOR] & [COLOR="Blue"]MaxDoubleTapTime[/COLOR] a value of [COLOR="blue"]120[/COLOR] & [COLOR="blue"]60[/COLOR] respectively seems to be the best I can do to allow double-top-drag to work with a slightly faster tap response, but not instant anymore.
[COLOR="green"]--------end update to myself---------[/COLOR]


I'm using Xubuntu 6.10 Edgy Eft, on Dell Inspiron 6400



[COLOR="Gray"]------------------------OLD LONG VERSION-----------------------------
I just switched to SimplyMepis6 .5 Beta 5 (now back to Xubuntu) as an alternative to Kubuntu and noticed that the tap response was 'instantaneous' after fresh install.

I looked into /etc/X11/xorg.conf

And noticed that with the following default settings, tapping is really fast, instantaneous.
[COLOR="DarkOrange"]Orange[/COLOR] means the text to take notice of.
-----------------------------
Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
  #commented stuff....
 InputDevice "Keyboard0" "CoreKeyboard"
 [COLOR="DarkOrange"]InputDevice "PS/2 Mouse" "CorePointer"[/COLOR]
 #commented stuff...
EndSection

Section "InputDevice"
  Identifier "PS/2 Mouse"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "false"
  Option "Emulate3Timeout" "70"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection
-----------------------------

That's all good [COLOR="Red"]but touch-scrolling doesn't work, 'double-click drag' doesn't work and 2 or 3 finger tap function cannot be set.[/COLOR] 

Then I start adding all the 'synaptics' stuff ([COLOR="Blue"]blue[/COLOR] means newly added) that people usually have, and I used to have on Ubuntu. See below:
------------------------------
Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
  #commented stuff....
 InputDevice "Keyboard0" "CoreKeyboard"
 InputDevice "PS/2 Mouse" "CorePointer"
 [COLOR="Blue"]InputDevice "Touchpad" "AlwaysCore"[/COLOR]
 #commented stuff...
EndSection

Section "InputDevice"
 Identifier "Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 #Option "SHMConfig" "on" #uncomment this line if u want to use qsynaptics/ksynaptics/gsynaptics
EndSection
----------------------------------
After I add the change, I ctrl+alt+backspace.

With the above setting, after tapping, it takes a bit less than a second to respond (which I used to put up with & thought it was normal). Installing qsynaptics and ksynaptics makes no difference in the speed.

The difference is noticeable with  [COLOR="Blue"]InputDevice "Touchpad" "AlwaysCore"[/COLOR] (very fast) and without it (slower).

So the question is :
[B]Why is tapping so slow with synaptics loaded?  Is there a way to make it faster?
Is there a way to enable scrolling Without synaptics loaded? (maybe enable 2 finger tap settings as well would  be a great bonus)[/B]

In the Gentoo wiki (referenced below), I followed every step even adding all the extra options (maxtaptime,etc.) under Section "InputDevice". Maybe changing one or two values of the options will make things faster?

Of course by simply pressing the left/right plastic buttons next to the touchpad is always very responsive. So this really is about just 'tapping'.

Hope you can help,
Thank you
 
I referenced from these:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)[/COLOR]

---

### Post by robin.com.au on 2007-02-20
bumpedy bump
Don't people like to use the tap feature?
I used to not like it cos i can accidentally select something when moving the cursor around
Then i got lazy, wanted to use just 1 hand with 1 finger, without moving away from the pad to click on the left/right-click plastic buttons.

Somehow, without the synaptics loaded, movin around with the touchpad is not really prone to accidental clicks, and is very snappy when trying to select/launch something. BUT I can't do all the features that synaptics offer, like touch-scroll, etc.

Help me have a better lazy tapping experience please.

Thank you,
Robin

---

### Post by robin.com.au on 2007-02-27
I kinda solved my problem.
I post problems in forums solely to seek help from myself.

Anyway.
Read the new information in the 1st post for the solution.
Still not perfect, cos im fussy. But could be useful to touchpad tapping linux users out there.

---

### Post by hermogene on 2007-03-31
Hi,
As I was not satisfied by double-tapping, I looked for informations and got [this]("http://lists.debian.org/debian-laptop/2005/11/msg00046.html"). As far as I understood, the MaxDoubleTapTime value should be greater than the SingleTap value. Those are my values:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver  "synaptics"
        Option  "SendCoreEvents"        "true"
        Option  "Device"                "/dev/psaux"
        Option  "Protocol"              "auto-dev"
        Option  "SHMConfig"             "true"
	Option	"RightEdge"		"5400"
	Option	"LeftEdge"		"1700"
	Option	"TopEdge"		"1200"
	Option	"BottomEdge"		"4200"
	Option	"FingerLow"		"20"	
	Option	"FingerHigh"		"30"
	Option	"MaxTapTime"		"80"
	Option	"MaxTapMove"		"220"
	Option	"MaxDoubleTapTime"	"100"
	Option	"ClickTime"		"1"
	Option	"FastTaps"		"false"
	Option	"VertEdgeScroll"	"true"
	Option	"HorizEdgeScroll"	"true"
	Option	"VertTwoFingerScroll"	"true"
	Option	"HorizTwoFingerScroll"	"true"
	Option 	"VertScrollDelta"	"100"
	Option 	"HorizScrollDelta"	"100"
	Option	"EdgeMotionMinZ"	"30"
	Option	"EdgeMotionMaxZ"	"160"
	Option	"EdgeMotionMinSpeed"	"15"
	Option	"EdgeMotionMaxSpeed"	"15"
	Option	"EdgeMotionUseAlways"	"0"
#	Option	"Repeater"		"/dev/ps2"
	Option	"MinSpeed"		"0.02"
	Option 	"MaxSpeed" 		"0.3"
	Option	"AccelFactor" 		"0.0200"
#	Option	"PressureMotionMinZ"	"10"
#	Option	"PressureMotionMaxZ"	"15"
#	Option	"PressureMotionMinFactor"
#	Option	"PressureMotionMaxFactor"
	Option	"UpDownScrolling"	"1"
	Option	"LeftRightScrolling"	"1"
#	Option	"UpDownRepeat"
#	Option	"LeftRightRepeat"
#	Option	"ScrollButtonRepeat"
	Option	"EmulateMidButtonTime"	"75"
	Option	"TouchpadOff"		"0"
#	Option	"GuestMouseOff"
	Option	"LockedDrags"		"true"
#	Option	"RTCornerButton"	"2"
#	Option	"RBCornerButton"	"3"
#	Option	"LTCornerButton"	"4"
#	Option	"LBCornerButton"	"5"
#	Option	"TapButton1"		"1"
#	Option	"TapButton2"		"2"
#	Option	"TapButton3"		"3"
	Option	"CircularScrolling"	"1"
	Option	"CircScrollDelta"	"0.1"
	Option	"CircScrollTrigger"	"1"
	Option	"CircularPad"		"false"
	Option	"PalmDetect"		"true"
	Option	"PalmMinWidth"		"10"
	Option	"PalmMinZ"		"200"
#	Option	"CoastingSpeed"		
	Option	"SingleTapTimeout"	"180"
EndSection
```

I enjoy the CircularScrolling (iPodlike scrolling), tell me if you found out some new clues for lazy tapping :)

---

### Post by robin.com.au on 2007-03-31
I played with MaxDoubleTapTime again and it turns out whatever value you give it, it does not really affect anything. What I think is more important is SingleTapTimeout. 

The lower value you give SingleTapTimeout, the quicker the single-tap responds, BUT you need to double-tap quickly in order for it to register. 

The higher value you give SingleTapTimeout, the slower the single-tap responds, BUT you can take your time to double-tap for it to register.

So it seems you cant have both 'fast single-tap' and 'silghtly slower double-tap' .

---

