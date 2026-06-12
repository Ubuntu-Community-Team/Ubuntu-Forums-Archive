---
title: "Synaptics Touchpad Config after Sleep Wakeup"
date: 2010-10-26
forum: Hardware
---

### Post by x201r on 2010-10-26
Hi All

I've been trying to get two-finger scrolling working on my newly installed 10.10 x64 on a Thinkpad x201.

After some searching around I was able to come up with a shell script to enable the two-finger scrolling but whenever I close the lid and return later the settings are gone. I tried placing my script in /etc/pm/sleep.d/ but even though it executes the settings do not return. I assume something else is overwriting my settings.

I guess the best way would be to make it into a udev script? I dont know how to convert these xinput commands into a udev script. Help with that, or any other way of accomplishing this goal would be greatly appreciated!

```
#!/bin/bash

sleep 5
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Two-Finger Scrolling' 8 1
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Two-Finger Scrolling' 8 1 1
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Two-Finger Pressure' 32 10
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Two-Finger Width' 32 8
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Edge Scrolling' 8 0 0 0

```

---

### Post by x201r on 2010-10-27
Wow! 5th page already.. Bump?

---

### Post by fenderr357 on 2010-10-27
I am having a similar problem while trying to keep two-finger scrolling working.

If I run this command in terminal,

```
synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinW=5 EmulateTwoFingerMinZ=48
```

Two-finger scrolling works fine. However, like you said.. it quits working upon resume. 

So I read around and found out that sleep.d scripts need a particular format, kinda like this:

```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        # ACTION BEFORE SUSPEND/HIBERNATE
        ;;
    thaw|resume)
        # ACTION AFTER RESUME
	synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinW=5 EmulateTwoFingerMinZ=48    
	 ;;
    *)
        ;;
esac
exit $?
```
But this script doesn't do anything from what I can tell.

I know this doesn't exactly help you, but it looks like we are in the same boat. It seems like the scripts are running before the touchpad gets initialized, causing the stuff that just got changed to be overwritten. 

I have also tried appending various sleep times:
```
thaw|resume)
        # ACTION AFTER RESUME
        sleep 10
	synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinW=5 EmulateTwoFingerMinZ=48       
	 ;;
```

Any ideas?

---

### Post by x201r on 2010-10-28
So I found out where to place it for Xorg, but even after adding it the Vert/Horiz scroll setting gets reset. One interesting thing is that everything other than the TwoFinger settings does not get reset.. Any thoughts anyone?

See the red sections below

```
[    16.095] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    16.095] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.095] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.095] (II) LoadModule: "synaptics"
[    16.095] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.095] (II) Module synaptics: vendor="X.Org Foundation"
[    16.095] 	compiled for 1.9.0, module version = 1.2.2
[    16.095] 	Module class: X.Org XInput Driver
[    16.095] 	ABI class: X.Org XInput driver, version 11.0
[    16.095] (II) Synaptics touchpad driver version 1.2.2
[    16.095] (**) Option "Device" "/dev/input/event6"
[    16.543] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    16.543] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4810
[    16.543] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.543] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    16.543] (II) SynPS/2 Synaptics TouchPad: buttons: left right middle
[COLOR="Red"][    16.543] (**) Option "SHMConfig" "on"
[    16.543] (**) Option "EmulateTwoFingerMinZ" "10"
[    16.544] (**) Option "EmulateTwoFingerMinW" "8"
[    16.544] (**) Option "VertTwoFingerScroll" "1"
[    16.544] (**) Option "HorizTwoFingerScroll" "1"[/COLOR]
[    16.703] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.703] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.793] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    16.793] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.793] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    16.793] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.793] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.973] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.974] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.974] (II) No input driver/identifier specified (ignoring)
```

I accomplished the above by putting the following into /usr/share/X11/xorg.conf.d/50-synaptics.conf

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        
        Option "SHMConfig" "on"
		Option "EmulateTwoFingerMinW" "8"
		Option "EmulateTwoFingerMinZ" "10"
		Option "VertTwoFingerScroll" "1"
		Option "HorizTwoFingerScroll" "1"
EndSection

```

---

### Post by x201r on 2010-11-18
Anyone have any ideas?

---

### Post by kslen on 2010-12-09
Create, set executable and edit the following file as root:
```
sudo touch /etc/pm/sleep.d/99-twofinger
sudo chmod 755 /etc/pm/sleep.d/99-twofinger
sudo nano /etc/pm/sleep.d/99-twofinger
```

Paste the following and edit /somewhere/your_twofinger_script.sh to match the location of your script as described by original poster:
```
#!/bin/sh
case "$1" in
        thaw|resume)
        DISPLAY=:0.0 su `who | grep tty7 | sed 's/\([a-z]*\).*/\1/'` -c '/somewhere/your_twofinger_script.sh'
        DISPLAY=:0.0 su `who | grep tty8 | sed 's/\([a-z]*\).*/\1/'` -c '/somewhere/your_twofinger_script.sh'
        ;;
        *)
        ;;
        esac
exit $?
```

You want the script to run both on tty7 and tty8 as 10.10 seems to change between the two every so often.

One might also want to remove any changes related to Z and W values in xorg.conf to avoid any quirks.

---

### Post by earlycj5 on 2010-12-09
I used Ptosiani's fix from this thread:
[http://ubuntuforums.org/showthread.php?t=1603657](http://ubuntuforums.org/showthread.php?t=1603657)

Direct link to post: [http://ubuntuforums.org/showpost.php?p=10071212&postcount=8](http://ubuntuforums.org/showpost.php?p=10071212&postcount=8)

This enabled it on startup/login and after suspend.

---

### Post by JeSTeR7 on 2011-04-04
I know this is an old thread, but I have to mention that after searching for days for a way to make scripts run after resume, kslen's post above worked perfectly!

---

### Post by DiZeee on 2011-06-02
Tried it on Ubuntu 11.04. Tests with "echo smthg to file" are ok, but xinput commands don't work.

---

### Post by DiZeee on 2011-06-02
Solved by renaming script from 99* to 0000* as scripts are executed in nomal order on suspend and in back order on resume

---

### Post by Stepan Roucka on 2012-09-15
I confirm that the answer of kslen combined with the advice of DiZeee to change the order of the scripts works on ubuntu 12.04 for setting xinput parameters on wakeup.

Thanks to both of you.

---

