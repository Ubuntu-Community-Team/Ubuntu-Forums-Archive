---
title: "HP G62 trackpad issue"
date: 2010-05-06
forum: Hardware
---

### Post by cooltd825 on 2010-05-06
I just bought the new HP G62 laptop, and the hardware support is generally pretty good on Ubuntu 10.04 64 bit with two exceptions.

The first is the audio card, which is a new Intel HDA 3400 series model.  It, though, is supported through a more recent Alsa driver that needs to be installed manually.  That isn't really a problem.

The biggest problem is the trackpad.  It's a standard Synaptics pad, but somehow the settings are all screwed up.  For general pointing operation, the support is just okay (the occasional mouse jump here and there), but there is one large horizontal section on the bottom of the trackpad where no touching is recognized.  I also cannot get the two finger scroll and two/three finger right click enabled.  I assume these are all just settings that are messed up, but without HAL or an xorg.conf I'm not sure where to start.  I've tried synclient to change the values, but they never seem to work for the two finger scroll.  I know two finger scroll is supported because it works fine under Windows.  

Any ideas?

---

### Post by cooltd825 on 2010-05-08
*bump*

---

### Post by jojohippo on 2010-06-05
Bump. Same issue on the HP g42...

---

### Post by cooltd825 on 2010-06-08
The trackpad is most likely identical.  Is your laptop newly purchased as well?

---

### Post by jojohippo on 2010-06-12
Yup, I week old. And it sounds like exactly the same issue, theres a dead spot on the bottom area of the trackpad and I can't get two finger scrolling to work. 

I also found the trackpad to be a bit jerky if I accidentally got two fingers on it at the same time. Adding this to xorg.conf seemed to help the jerkiness but not the other issues
[INDENT]Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "auto-dev"
    Option         "AlwaysCore" "true"
    Option         "CorePointer"
    Option         "SHMConfig" "true"
#disable edge scroll
    Option         "VertEdgeScroll" "1"
    Option         "HorizEdgeScroll" "1"
#other options
    Option         "VertTwoFingerScroll" "0"
    Option         "HorizTwoFingerScroll" "0"
    Option         "PalmDetect" "1"
    Option         "LockedDrags" "1"
    Option         "LockedDragTimeout" "750"
EndSection[/INDENT]

This is how I added an xorg.conf: [http://ubuntuforums.org/showthread.php?t=1428788]("http://ubuntuforums.org/showthread.php?t=1428788")

Have you had any better luck?

---

### Post by RocketParrot on 2010-06-14
I am whit the same problem but i can't fix the sound
how did you did it?

---

### Post by jojohippo on 2010-06-14
This tutorial worked for me: [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")

---

### Post by Borjs85 on 2010-06-22
Something new about the trackpad issue?

In windows 7 multitouch works great... I don't know if that will be possible in ubuntu, but at least i'd be pleased with a normal trackpad without a dead zone.

Thanks in advance

---

### Post by jojohippo on 2010-06-28
A few updates on the trackpad:

1. I was able to get two finger scroll working using the instructions here: [http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html]("http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html").

My script looks like this
[INDENT]sleep 30
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
synclient VertEdgeScroll=0
synclient TapButton2=2 TapButton3=3[/INDENT]

The 'sleep 30' delays the script by 30 seconds, I found this was necessary when adding it to system> preferences> startup applications. Without the delay the script just wouldn't work and I'd have to run it manually

The 'synclient VertEdgeScroll=0' disables edge scrolling if you want that.

The 'synclient TapButton2=2 TapButton3=3' makes two finger taps a middle click rather than a right click.

I found the trackpad wasn't jumpy anymore after adding this so the changes I had previously made to xorg.conf weren't really necessary for me.


2. Just out of curiosity I downloaded and tried the 10.10 Maverick Meerkat livecd and the entire trackpad works! :) I can live with 4/5ths of a trackpad for now.

---

### Post by Borjs85 on 2010-06-29
Oh, thank you!
I'll try this this evening :guitar:

---

### Post by cooltd825 on 2010-06-30
Just as an update after some testing...

I can't figure out a way to get two finger anything to work, nor can I get the jumpiness to stop.  The one thing I do have working is the entire trackpad!  I installed Fedora 13 for stability reasons and found this pleasant surprise.  Here are my "synclient -l" values, if they're of any use to anyone using this model of HP.


LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0

---

### Post by C-guy on 2010-07-12
[QUOTE=]I just bought the new HP G62 laptop, and the hardware support is generally pretty good on Ubuntu 10.04 64 bit with two exceptions.

The first is the audio card, which is a new Intel HDA 3400 series model.  It, though, is supported through a more recent Alsa driver that needs to be installed manually.  That isn't really a problem.[QUOTE=]

Could you please say exactly which driver?

---

### Post by cooltd825 on 2010-07-12
I'm not sure what's on my system now (just did a fresh install to verify), but I must install driver version 1.0.23 to fix.

---

### Post by Borjs85 on 2010-07-13
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script)

Easy way to upgrade alsa.

---

### Post by cooltd825 on 2010-07-19
Thanks Borjs.  I'm back on Fedora now anyway, which includes the driver as default.

But to the juicy part of today's post...  I've been able to solve (sort of) our two finger scroll issue!  It's not true multi touch recognition, but the emulation our driver does is satisfactory.  This seems to be a pretty big issue on newer netbooks which really need the multi touch gestures.  Anyway, it just depends on putting the correct values in for the emulation.  I also disabled the horizontal and vertical zone scrolling, and it works fine.  Make sure you enable Vertical and Horizontal Two Finger Scroll in synclient or whichever method you use.  

anyway, here's the script I use

```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 40
```

---

### Post by cooltd825 on 2010-07-20
I'm at a complete loss for words...  I did a few reboots to test if it was working, and it did every time.  

I didn't touch the computer for a few hours (it was off), and all of a sudden I can't get this thing to work.  The cursor is all jumpy when I put two fingers down.

---

### Post by Charbs on 2010-08-10
Ive tried everything in this thread and nothing will get ubuntu to see 100% of my trackpad, let alone even come close to getting two finger scrolling to work. I think I might have to return this G62 cuz its way too frustrating unless you hook up a mouse.

Is there anyone who has had success with this touchpad?

---

### Post by mannyweb.ca on 2010-08-10
^ I also recently purchased the HP G62 and yes the trackpad is kind of jerky, but overall no issues with it my main beef has been with Audio and most recently the webcam.  I updated Alsa and it was working for a couple of days but now all of a sudden whenever I try to make a recording requiring the internal mic it goes to hell and the webcam was working aswell, but now everywhere I try to use it, it tells me that my webcam is already in use.

I invoke the Ubuntu Community to my aide!

---

### Post by cooltd825 on 2010-09-30
Sorry about the late response.

As for your trackpad not being 100%, don't worry about it.  It's just the driver version they are using.  It'll be upgraded to what newer distributions use when the 10.10 release comes.  You can try the beta for now if you want, it'll work.  I myself am waiting for the final release so my packages don't get too messed up going from beta.  I've tried to update the single driver associated with the trackpad, but it's nearly impossible due to all the dependencies it requires you to obtain. 

as for two finger scroll, I'll mess around a little bit after Meerkat is out.  good luck!

---

### Post by Borjs85 on 2010-12-23
For everyone interested: there is already a fix that really works!!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191)

The comment 116 has attached a deb file that will solve all our issues. Even you can select two finger scroll in the mouse preferences.

---

### Post by loonysalmon on 2010-12-30
After doing some reading, I have been seeing that loads of people have been having trouble with their sound not working.  Using the dist-upgrade also upgrades ALSA to 1.0.23 and fixes that.

I did need to fix the synaptics driver by installing the .deb at comment #167 in [this thread]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191") on launchpad.  The comment can be found [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167")

After installing the .deb I went into system->preferences->mouse and in the trackpad tab I enabled the two finger scrolling.  After doing this there was a lot less jumpiness and it has been working just fine since. :)

I hope this works for you and I wish you the best of luck.  Hopefully you have subscribed to this and will find this thread again. :)

-Tom

---

### Post by loonysalmon on 2011-01-04
I wanted to point out that I was having a few more frustrations with the trackpad so I decided to do a little more digging to find the answers I was searching for.  I kept on having my settings changed for disabling the RTCornerButton and RBCornerButton in synclient's settings so I ended up finding a package called

'gsynaptics'.  It managed to take care of everything I wanted and it was a nice configuration utility to use within gnome.  After installation it can be launched with 'gpointing-device-settings'.

Hope this helps!

-Tom

---

