---
title: "Disable PS2 mouse while typing (or fix touchpad detection)"
date: 2011-05-25
forum: Hardware
---

### Post by Naggobot on 2011-05-25
I think that due to 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

and in case of Elan touchpads(filed by me)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/788109](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/788109)

and (from above)
[https://bugzilla.kernel.org/show_bug.cgi?id=27442](https://bugzilla.kernel.org/show_bug.cgi?id=27442)

it is not possible to configure the Elan smart-pad touch pad. I do not mind the fancy features since I have never used those and even tap/drop works but

I would like to disable the touch pad while typing

Since the touch pad is not detected it is not possible to use syndaemon.

Any ideas?

I tagged this as all variants since this probably affects all distros since indication is that it is a kernel bug. I use Ubuntu Lucid 10.04.

---

### Post by Naggobot on 2011-05-25
It seems that Natty would be a fix but I want to stay with Lucid. I tested Natty with LiveUSB and in Natty there was a touchpad tab in mouse preferences.

I am pretty confident that it is a kernel bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192)

and

[https://bugs.launchpad.net/ubuntu/+bug/777424](https://bugs.launchpad.net/ubuntu/+bug/777424)

so it is likely that there is no easy fix to touchpad detection but is there an easy fix to disable the touchpad (i.e mouse) while typing?

---

### Post by AureiAnimus on 2011-05-25
To turn the touchpad on and off with a shortcut:
I followed this: [http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433) 
until "Making the magic happen automatically:" and then linked the script to a shortcut.


You might need to alter the number 7 here in the line that defines the touchpadID, since that's dependent on the number of spaces in the name. 
```
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $7}' | awk -F "=" '{print $2}')
```

I also fixed touchpad while typing, but I did not really code that properly, so I have 3 bash scripts and two python scripts with direct references to the directory they're in all over them. If the shortcut doesn't cut it, say so and I'll post them, but that's not exactly an "easy fix".

---

### Post by Naggobot on 2011-05-26
Hmm

it seems that

```
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')

```does not return correct ID since the line

```
xinput --set-prop $touchpadID "Device Enabled" 0

```returns an error

```
xinput -list
```oputput

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```and I have modified the script

```
touchpadString="Logitech"
```and if I input this to terminal

```
xinput list | grep Logitech | awk -F " " '{print $6}' | awk -F "=" '{print $2}'
```I get nothing as output but if I run

```
xinput --set-prop 12 "Device Enabled" 0
```touchpad is turned off and even if I hard code

```
touchpadID="12"
```is still get the error

```
./toggleTouchpad.sh: line 74: [: -eq: unary operator expected
```I have not installed havlevt but I do not think that is the reason.

Can it be that the xinput --set-prop does not accept string variable?

---

### Post by AureiAnimus on 2011-05-26
I think that might be the case.

What I did was just try this line in the terminal
xinput list | grep Logitech | awk -F " " '{print $6}' | awk -F "=" '{print $2}'
while changing the number where there is a 6 now. In my case it was 7, in your case it might be more or less. I think that using this line with the correct number should solve the problem that you're having (I recall having the same problem)

---

### Post by Naggobot on 2011-05-26
Excellent!

Lucky number 7 does the trick. Next to add a hotkey. I post hat I did when ready or revert if I run in to problems.

---

### Post by Naggobot on 2011-05-26
I moved the script to /bin and added a hot key to System->preferences->keyboard shortcuts. For command I just used the script name.

I first tried to use alt+space but it did not work for some reason. Super+alt+space works.

I am not fluent with the scripts so I need to ask if there are any pointers to an extremely easy way to make this so that

1. The script runs as a daemon
2. Script listens to keyboard event (maybe with [http://gizmod.sourceforge.net/](http://gizmod.sourceforge.net/))
3. If the script detects keyboard event the PS2 mouse is disabled until no more keyboard events are detected.

Maybe the Gizmod alone would be enough with a correct [configuration]("http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Tutorial_-_Step_by_Step_-_Creating_a_new_application_event_mapping") script? At least the example looks like it. 

In pseudo we would have something like

```

INTERESTED_CLASSES = [Gizmod.Keyboards]
if Event.Class in INTERESTED_CLASSES and Event.Value != 0 \  
  if Touchpadoff !=1 
     set TouchpadOff=1
     touchpadString = "Logitech"
     touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $7}' | awk -F "=" '{print $2}')
     xinput --set-prop $touchpadID "Device Enabled" 0
     touhpadDelay = 1
     sleep touchpadDelay
     xinput --set-prop $touchpadID "Device Enabled" 1
     set TouchpadOff=1
     endif
endif

```Is there any idea in this and does there happen to be anyone with same problem and 
competent enough to try this out

---

### Post by AureiAnimus on 2011-05-27
You can try my scripts with a little effort if you want to. 

I suggest the following approach:
Place in ~/bin, change all mentions in the script of /home/pim/bin
to /home/username/bin (I'd too that myself, but I don't have the time atm), make all of the files excecutable. Then to test, excecute toggleSwitchInit, then toggleTouchpad, which should result in the touchpad being toggled "ON", "OFF" or "SWITCH", which is reported with a message. Switch should make sure the touchpad doesn't work while typing. The touchpad delay parameter in your code can be found in "toggleSwitchInit", but lowering it any further than 1 sec may introduce a bug. 

If it works, add toggleSwitchInit to your startup applications and point a shortcut to toggleTouchpad

What this does, is the python script is called twice and launches two processes. One checks for keypresses and notes down the time in a hidden file. The second compares the current time to the time in the file and if Switch-mode is on and the current time is less than touchpadDelay after the file-time, the touchpad is turned off, if it's longer, it's turned on. toggleTouchpad enables switching between switch, on and off. toggleTouchpad-forscript is for the switchable mode, since toggleTouchpad cannot be used since that would turn off the switchable mode itself. pyxhook is a script that's part of the pykeylogger library, which enables listening for events.

---

### Post by Naggobot on 2011-05-28
Thanks

I rummage through those when I have time and revert back here when I have done that.

---

### Post by MarjaE on 2011-05-28
I'm having a similar problem with the ALPS Glidepoint. I'm not sur if it's exactly the same problem, but so far installing symantiks has not worked, editing the grub to add i8042 variations has not worked, editing the xorg.conf.d has not worked, etc.

One of the early changes made a trackpad tab appear under the mouse preferences, but had no effect on the pad's behavior.

I tried a mouse configuration utility, but it was unable to distinguish left button clicks fro taps, registering both as button1 clicks.

Getting into alps-specific territory, which may not apply to the elan trackpads, linux developers argued about whether alps.c should enable tapping by default, making it IMPOSSIBLE to disable tapping without disabling the mouse, or disable tapping by default, making it possible to use the computer but slightly harder to enable tapping in software. They chose to enable tapping by default and I'm stuck with a computer which erratically clicks wherever it is dragged and erratically moves the typing location whenever one tries to type.

At least disabling the mouse while typing would restore some functionality. But tap-to-click makes it much harder to use the GUI. [/rant] Sorry I've been trying to debug this since monday.

---

### Post by AureiAnimus on 2011-05-29
> **Naggobot said:**
> Thanks

I rummage through those when I have time and revert back here when I have done that.

Okay. One other thing: Don't forget to change to your touchpadString in toggleTouchpad and toggleTouchpad-forscript, the 7 is already there.

> **MarjaE said:**
> I'm having a similar problem with the ALPS Glidepoint. I'm not sur if it's exactly the same problem, but so far installing symantiks has not worked, editing the grub to add i8042 variations has not worked, editing the xorg.conf.d has not worked, etc.

One of the early changes made a trackpad tab appear under the mouse preferences, but had no effect on the pad's behavior.

I tried a mouse configuration utility, but it was unable to distinguish left button clicks fro taps, registering both as button1 clicks.

Getting into alps-specific territory, which may not apply to the elan trackpads, linux developers argued about whether alps.c should enable tapping by default, making it IMPOSSIBLE to disable tapping without disabling the mouse, or disable tapping by default, making it possible to use the computer but slightly harder to enable tapping in software. They chose to enable tapping by default and I'm stuck with a computer which erratically clicks wherever it is dragged and erratically moves the typing location whenever one tries to type.

At least disabling the mouse while typing would restore some functionality. But tap-to-click makes it much harder to use the GUI. [/rant] Sorry I've been trying to debug this since monday.

Did you try the instructions i posted a little up? That should work to turn it off.

---

### Post by Naggobot on 2011-05-29
To MarjaE

ALPS seems to be a huge pain for other also. I trust you have noted

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

Overall launcpad returns 50 bugs related to ALPS touch pads. At least Elan works ok othervise except disabling the touchpad while typing. 

About: " erratically clicks wherever it is dragged"

I do not know but might drag and drop sensitivity affect this a bit if you turn it to maximum?

---

### Post by MarjaE on 2011-05-29
> **AureiAnimus said:**
> Did you try the instructions i posted a little up? That should work to turn it off.

I couldn't get them to work. My brother is more experienced with Linux, and he's trying to get that to work. I'm still using my old computer right now.

> **Naggobot said:**
> To MarjaE

ALPS seems to be a huge pain for other also. I trust you have noted

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

Overall launcpad returns 50 bugs related to ALPS touch pads. At least Elan works ok othervise except disabling the touchpad while typing.

Yep.

> About: " erratically clicks wherever it is dragged"

I do not know but might drag and drop sensitivity affect this a bit if you turn it to maximum?

Okay. I had turned one of the other sensitivity controls to the minimum, but that one was still at default/maximum.

Thanks.

---

### Post by MarjaE on 2011-05-29
Aurei,

My brother rewrote the scripts because the computer reads the trackpad as a ps/2 mouse, instead of as a trackpad. It now works in the command line. I tried a dozen different ways to get this to work with either keyboard shortcuts or autokey, but could get neither one to work, partly because I couldn't decode the documentation for them.

Also, I see how to toggle it on or off, but you mentioned there was some way to toggle it to switch?

---

### Post by MarjaE on 2011-05-29
Okay, now the hotkeys are working. It should work okay for now.

---

### Post by Naggobot on 2011-06-01
Instructions on (something) can be found from 

[https://launchpadlibrarian.net/72674579/touchpad](https://launchpadlibrarian.net/72674579/touchpad)

this is related to launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192) and is a suggested solution. I have not yet tried but if I understand right it includes compiling a new psmouse module.

---

### Post by MarjaE on 2011-06-01
I just upgraded back to 11.04 and it has broken the hotkey w/o fixing the problem. :(

---

### Post by Naggobot on 2011-06-02
I tried the instructions from 
[https://launchpadlibrarian.net/72674579/touchpad](https://launchpadlibrarian.net/72674579/touchpad)

when applying the patch with 
```
patch -p1 < 01elantech_2.6.38.patch
```

I get

```

    patching file drivers/input/mouse/elantech.c
    Hunk #2 FAILED at 14.
    Hunk #3 FAILED at 22.
    Hunk #4 FAILED at 41.
    Hunk #5 FAILED at 66.
    Hunk #6 succeeded at 73 (offset -7 lines).
    Hunk #7 succeeded at 139 (offset -7 lines).
    Hunk #8 FAILED at 164.
    Hunk #9 succeeded at 173 (offset -7 lines).
    Hunk #10 succeeded at 199 (offset -7 lines).
    Hunk #11 FAILED at 223.
    Hunk #12 FAILED at 256.
    Hunk #13 FAILED at 301.
    Hunk #14 succeeded at 307 (offset -12 lines).
    Hunk #15 FAILED at 328.
    Hunk #16 FAILED at 460.
    Hunk #17 FAILED at 518.
    Hunk #18 FAILED at 534.
    Hunk #19 succeeded at 565 (offset -34 lines).
    Hunk #20 FAILED at 655.
    Hunk #21 FAILED at 696.
    Hunk #22 FAILED at 748.
    Hunk #23 FAILED at 778.
    Hunk #24 FAILED at 832.
    Hunk #25 succeeded at 793 (offset -54 lines).
    17 out of 25 hunks FAILED -- saving rejects to file drivers/input/mouse/elantech.c.rej
    patching file drivers/input/mouse/elantech.h
    Hunk #5 FAILED at 91.
    1 out of 5 hunks FAILED -- saving rejects to file drivers/input/mouse/elantech.h.rej

```

which does not look good. 

After this making with
```
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=`pwd` drivers/input/mouse/psmouse.ko
```

gives
```
    make: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
      CC [M]  /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/psmouse-base.o
      CC [M]  /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/synaptics.o
      CC [M]  /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/alps.o
      CC [M]  /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.o
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c: In function ‘elantech_sliced_command’:
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:85: error: ‘ETF5900’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:85: error: (Each undeclared identifier is reported only once
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:85: error: for each function it appears in.)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c: In function ‘elantech_read_reg’:
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:126: error: ‘ETF5900’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:133: error: ‘ETF020022’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:134: error: ‘ETF020600’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:142: error: ‘ETF020030’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:143: error: ‘ETF0208’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:144: error: ‘ETF020B00’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:145: error: ‘ETF0402’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:146: error: ‘ETF0401’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:147: error: ‘ETF0403’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:148: error: ‘ETF1400’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c: In function ‘elantech_write_reg’:
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:178: error: ‘EF_023_DEBUG’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:186: error: ‘ETF5900’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:192: error: ‘ETF020022’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:193: error: ‘ETF020600’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:202: error: ‘ETF020030’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:203: error: ‘ETF0208’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:204: error: ‘ETF020B00’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:205: error: ‘ETF0402’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:206: error: ‘ETF0401’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:207: error: ‘ETF0403’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:208: error: ‘ETF1400’ undeclared (first use in this function)
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c: In function ‘elantech_report_absolute_v2’:
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:310: warning: unused variable ‘etd’
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c: In function ‘elantech_set_int_attr’:
    /home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.c:568: error: ‘ETF020030’ undeclared (first use in this function)
    make[1]: *** [/home/myhome/src/linux-source-2.6.32/drivers/input/mouse/elantech.o] Error 1
    make: *** [drivers/input/mouse/psmouse.ko] Error 2
    make: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'

```

which looks bad enough for me not to even try the module.

---

### Post by Naggobot on 2011-06-09
There seems to be a kernel backport ppa for lucid. 

[https://launchpad.net/~canonical-kernel-team/+archive/ppa](https://launchpad.net/~canonical-kernel-team/+archive/ppa)

there is a version                  linux-lts-backport-natty                                               2.6.38-10.44~lucid1  available.

Anyone has dared to install this?

I am just wondering since 2.6.38 should have the touchpad recognition fixed

---

### Post by Naggobot on 2011-07-18
Latest upgrade to kernel 2.6.32-33-generic fixed the issue at least for me and now the touch pad tab is visible in the mouse preferences. 

I added also comment to the Launchpad bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192?comments=all)

---

