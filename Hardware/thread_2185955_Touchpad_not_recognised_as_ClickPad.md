---
title: "Touchpad not recognised as ClickPad"
date: 2013-11-05
forum: Hardware
---

### Post by amorosicky on 2013-11-05
Hi everybody
I bought a new asus s56ca notebook with an elantech ETPS/2 Touchpad with integrated buttons. Unfortunately the Touchpad hasn't been recognises as ClickPad. So as example, it is not possible to move an item while pressing the left button. And it's very hard to do a doubleclick because the cursor is moving when trying to press the button. I hope you'll understand what i mean. I tried many different things which should work for Ubuntu 12.04. But all the things i've tried didn't work on my Ubuntu 13.10. I really hope that someone could help me before I'm throwing my notebook out of the window :D
Many thanks

robin

---

### Post by varunendra on 2013-11-06
Welcome to the forums amorosicky! :)

I have an Asus X54C with same touchpad, works fine with 12.04 here. Please post back outputs of a few commands to let me see what all is different in your setup.

Open a terminal (Ctrl-Alt-T) and enter these commands (you may copy-paste) -
```
uname -mr
lsb_release -d
xinput
synclient
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by amorosicky on 2013-12-05
hey, thanks for your post. here's the output of the Terminal: 
```

robin@ordenador:~$ uname -mr
3.11.0-14-generic x86_64
robin@ordenador:~$ lsb_release -d
Description:    Ubuntu 13.10
robin@ordenador:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
robin@ordenador:~$ synclient
Parameter settings:
    LeftEdge                = 129
    RightEdge               = 3120
    TopEdge                 = 120
    BottomEdge              = 2103
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 173
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 78
    HorizScrollDelta        = 78
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.050813
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 1
    RightButtonAreaLeft     = 1624
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1822
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0
robin@ordenador:~$ lsmod

```
I also read, that I can add a dead zone (AreaBottomEdge) to my clickpad. But I've got also some other Problems with ClickPad: I can't change the pointer speed (I can change the value, but nothing happens). "Disable while typing" also doesn't work...grrrr :D it's annoying
peace

PS: just recognised that changing the pointer speed and "disable while typing" work now. Don't know why, didn't work 2 months ago ;) so, setting a "dead zone" would be an option, but maybe there is a better way? ;-)
thanks

---

### Post by varunendra on 2013-12-06
Seeing the last lines in the output of synclient, it seems you have already tried some custom settings. Either that, or the touchpad has not been detected as a normal ETPS/2 Elantech Touchpad at all, because there are many settings that are entirely missing as per synclient output (apart from some extra ones in the last).

The command "xinput" provides an option to 'create' some settings if we know the correct data types, but they will work only if the touchpad actually has those properties and the controlling driver is functioning well. I have never tried that before and don't know if this would be of any help at all.

You may try a driver parameter for now -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

Have you tried 12.04.3 yet?

---

### Post by amorosicky on 2013-12-09
Actually, I'm not sure if I've changed some settings ^t^ I've already tried other things (when I asked google how to make my clickpad work), therefore I've probably changed some settings. I tried these driver parameters. And it's the first time that moving, while pressing the left button, works. but feels know very 'unnatural' ,  "disable while typing" doesn't work anymore and the pointer speed is very slow, but a lot of acceleration. I've not tried 12.04, but 12.10

cheers

---

### Post by varunendra on 2013-12-09
You may try installing "gpointing-device-settings" to see if it can provide you sufficient control over the pointer -
```
sudo apt-get install gpointing-device-settings
```

Although it is a GUI program, yet if you are using Unity desktop interface, you will have to run it via terminal command or **Alt-F2 > gpointing-device-settings**.

By the way, unless you have manually upgraded the kernel and Xorg components in 12.10, 12.04.3 includes a much newer version of both the kernel and Xorg packages. If you wish to try it, I'd recommend to download it via torrent to ensure integrity as well as a faster download : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) , then either burn a CD or create a live USB with the ISO and test it in Live mode to see if it works well.

---

### Post by amorosicky on 2013-12-26
thanks for your help. I tried 12.04 but didn't work. I also tried gpointing-device-settings without success. I still can't put one finger on the button and move (maybe i can add a "dead-zone" somehow?) and disable while typing also doesn't work. I have no idea what to do :( it's annoying

---

### Post by varunendra on 2013-12-26
> **amorosicky said:**
> I have no idea what to do :( it's annoying

Neither do I at this point. But was the output of "synclient" command same on 12.04 live? If no, trying the same tricks you tried earlier (the xinput and modprobe commands) may work there. If so, they should work on the installed system as well, with no customization like your original synclient output suggested.

---

### Post by caymus on 2013-12-26
You need to configure your touchpad into:

/usr/share/X11/xorg.conf.d/50-synaptics.conf ,i thing.

I dont see another conf file path for this, into ubuntu.

[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

It is how i tweak my touchpad into archlinux, i have ubuntu on one desktop only, sorry, i cannot test on ubuntu.

Maybe someone with touchpad can help further.

---

