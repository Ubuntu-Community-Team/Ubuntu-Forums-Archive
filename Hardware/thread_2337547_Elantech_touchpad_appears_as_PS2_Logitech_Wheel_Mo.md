---
title: "Elantech touchpad appears as PS/2 Logitech Wheel Mouse"
date: 2016-09-19
forum: Hardware
---

### Post by auggydioz on 2016-09-19
[TABLE]
[TR]
[TD="class: votecell"][CENTER]up vote[COLOR=#6A737C]0[/COLOR]down vote[favorite]("http://askubuntu.com/questions/826937/elantech-touchpad-appears-as-ps-2-logitech-wheel-mouse#")
[/CENTER]
[/TD]
[TD="class: postcell"]I have a Lenovo Y700 laptop with Ubuntu 16.04 installed and I have a several issues connected with Elantech touchpad that is installed on this laptop model.

First of all, answers from [this question]("http://askubuntu.com/questions/331130/mercury-avatar-elantech-touchpad-multitouch-and-gesture-are-not-supported") did not help me (can't compile drivers). From the other question I found that they are not compatible with my kernel and I found there a 'fixed' version that did compile yet still didn't help me.

Touchpad seems to be working when the following touchegg config loads:

synclient ClickFinger3=0
synclient TapButton3=0
touchegg &

It does loads only after a system update (if anything gets updated).

I guess the issue is somehow connected with my Razer Deathadder 3500 DPI mouse. If the system gots updated and I use only touchpad it seems to work correctly. But after plug/unplug of the mouse all goes bananas.
Fix for /etc/default/grub from [this answer]("http://askubuntu.com/questions/786021/ubuntu-16-04-elantech-touchpad?rq=1") also doesn't help. Neither does editing 50-synaptics.conf from [this answer]("http://askubuntu.com/a/795320/255074").

Here are some system info that should help:

xinput:
     Virtual core pointer                       id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                 id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=10   [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                         id=11   [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                     id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]

lsinput (only mouse detection part):

/dev/input/event14
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x1
   version : 99
   name    : "PS/2 Logitech Wheel Mouse"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_REL

The mouse detect properly and listed in lsusb as razer mouse. Yet rezercfg fails to detect it.

Module psmouse is loaded during the startup. After system login or executing .xprofileconfiguration from console I get:

Couldn't find synaptics properties. No synaptics driver loaded?

I can provide additional information on your request.

Any help is appreciated as I don't have enough time now to switch to Arch Linux (where as a rule of thumb everything works correctly).

[/TD]
[/TR]
[/TABLE]

---

