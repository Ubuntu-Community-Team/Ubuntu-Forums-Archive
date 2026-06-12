---
title: "Lenovo Thinkpad Yoga Kubuntu 13.10"
date: 2013-12-12
forum: Hardware
---

### Post by risto.pekkala2 on 2013-12-12
So. Here I sit and fiddle with this nice laptop of mine. Factory disk setup cloned. UEFI disabled. Kubuntu 13.10 desktop installed. Win 8.1 running in VirtuaBox. 

This is the business variant of Yoga. The screen (12.5") is foldable backwards so that keyboard and screen are back to back. The keyboard locks mechanically when folded. 

Things that work:
Display in full 1920x1080
USB 3 Ethernet dongle
USB
Keyboard
Sound
Wireless
Bluetooth

Things that don't quite work:
Wacom pen and touch, no pressure, no finger klick
Multitouch
Autorotate screen

Not tested:
sdcard reader
Fingerscanner - has no

I don't know how to help make this laptop fully compatible with Linux. What should I try? 

Mind that this will to be my work laptop so I rather not break it ones a week. Twice is ok. :-)

/ Risto Pekkala

IT-manager 
[www.teknikenshus.se]("http://www.teknikenshus.se")

---

### Post by risto.pekkala2 on 2013-12-16
Finger klick works after Unity desktop was installed and removed.

---

### Post by jon_mease on 2013-12-17
Hi, I don't have a thinkpad yoga yet and my interest in getting one is dependent on its Linux compatibility.
     The author of the following thread also cited problems with the web-cam and with getting the thinkpad yoga to wake from sleep/hybernation.
[http://forums.lenovo.com/t5/Linux-Discussion/Thinkpad-Yoga-A-few-issues-webcam-hibernate-and-screen-wake/td-p/1341849]("http://forums.lenovo.com/t5/Linux-Discussion/Thinkpad-Yoga-A-few-issues-webcam-hibernate-and-screen-wake/td-p/1341849")

Have you tried these?  It would be nice to have a full running list of compatibility problems.

Regarding pressure sensitivity. Could you post the output of running the following in the terminal:
> 
xsetwacom --list devices


and then run the following command, but replace "Wacom Bamboo Connect Pen stylus" with the name of the stylus device returned in the previous command.
> 
xsetwacom --get "Wacom Bamboo Connect Pen stylus" all


The results of this second command might give us some clues as to what is going on.
-Jon

---

### Post by Sheldor on 2013-12-18
Hi,

I just bought one too, but i am not sure if i will keep it, can't get palm detection working. Can't write anything with it, it always recognises my palm as input. Very anoying.

Anyhow here is the output you requested:

> xsetwacom --get "Wacom ISDv4 EC Pen stylus" all
Option "Area" "41 -22 27692 15572"
'Button' requires exactly 1 value(s).
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "2"
Option "RawSample" "4"
Option "PressureCurve" "0 0 100 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "on"
Option "Gesture" "off"
Option "ZoomDistance" "0"
Option "ScrollDistance" "0"
Option "TapTime" "250"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "Threshold" "27"
Option "ToolType" "348"
Option "ToolSerial" "0"
Option "ToolID" "0"
Option "ToolSerialPrevious" "1"
Option "BindToSerial" "0"
Option "TabletID" "236"

---

### Post by jon_mease on 2013-12-20
Thanks for posting this output and sharing your experience with Palm rejection. Your output looks very similar to mine with a working wacom bamboo external tablet. 

If you do return it I'd be curious to hear what you do instead. 

Based on all of the reported hardware issues with the Thinkpad Yoga on Linux i'm starting to lean towards just using one of the new medium-sized intuos pro tablets with a dell XPS 13 developer edition.

---

### Post by djahma on 2013-12-30
It felt good finding this thread when struggling with our new machine, no I am not alone:smile:

So  while there are many scripts out there to rotate the screen, I  absolutely wanted the STMicro sensor-hub to work and rotate the screen  for me. I failed there](*,)
Therefore I took bytes of shell scripts here and there to achieve the perfect setup for my Yoga.

First,  is the famous script to rotate the screen 90degrees at a time and  rotate the touchscreen and pen input also. I saved that to  ~/scripts/TPYoga_Rotate.sh and associated it with keyboard shortcut  Meta+O which occurs to be the keycode for the physical screen lock  button. That script also disable the touchpad when orientation is different from laptop mode
```
#!/bin/bash

# Script rotates screen 90deg on every run, and also rotates touchscreen and wacom input.
# In modes other than normal, touchpad is deactivated.

current_orientation(){
    xrandr|grep " connected" |awk '{print $4}'
}
#orientation=`current_orientation`
case $( current_orientation ) in
    "(normal" )
        xrandr -o left
        xsetwacom set "Wacom ISDv4 EC Pen stylus" rotate ccw
        xsetwacom set "Wacom ISDv4 EC Pen eraser" rotate ccw
        synclient TouchpadOff=1
        xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axes Swap" "1"
        xinput set-prop "ELAN Touchscreen" "Evdev Axis Inversion" 1 0
        onboard &
        ;;
    "inverted" )
        xrandr -o right

        xsetwacom set "Wacom ISDv4 EC Pen stylus" rotate cw
        xsetwacom set "Wacom ISDv4 EC Pen eraser" rotate cw
        xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axes Swap" "1"
        xinput set-prop "ELAN Touchscreen" "Evdev Axis Inversion" 0 1
        ;;
    "right" )
        xrandr -o normal
        xsetwacom set "Wacom ISDv4 EC Pen stylus" rotate none
        xsetwacom set "Wacom ISDv4 EC Pen eraser" rotate none
        synclient TouchpadOff=0
        xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axes Swap" "0"
        xinput set-prop "ELAN Touchscreen" "Evdev Axis Inversion" 0 0
        killall onboard
        ;;
    "left" )
        xrandr -o inverted
        xsetwacom set "Wacom ISDv4 EC Pen stylus" rotate half
        xsetwacom set "Wacom ISDv4 EC Pen eraser" rotate half
        xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axes Swap" "0"
        xinput set-prop "ELAN Touchscreen" "Evdev Axis Inversion" 1 1
        ;;
    * )
        synclient TouchpadOff=0
        echo "c est autre chose"
        current_orientation
        #echo $orientation
        ;;
esac
```

Next is a script to disable the touchscreen when the pen is in proximity. I saved that to ~/scripts/TPYoga_PenInOut.sh and set it to start with the system. With that, I can rest my hand on the screen when using the pen, AND THAT IS AWESOME!!\\:D/
```
#!/bin/bash

# Deactivate touchscreen when wacom pen is in proximity
# Activate touchscreen when wacom pen gets out

sleeptime="0.5s"
lastPenPosition="Proximity=Out"
while true
do 
    mssg="`xinput query-state "Wacom ISDv4 EC Pen stylus" | grep Proximity`"
    if [ ${#mssg} -gt 1 ]
    then
        inout="`echo $mssg | awk '{print $3}'`"
        case "$inout" in
            "Proximity=In" )
                if [ $lastPenPosition != $inout ]
                then
                    xinput --disable "ELAN Touchscreen"
                    lastPenPosition=$inout
                fi
                ;;
            "Proximity=Out" )
                if [ $lastPenPosition != $inout ]
                then
                    xinput --enable "ELAN Touchscreen"
                    lastPenPosition=$inout
                fi
                ;;
        esac
    fi
    sleep $sleeptime
done
```
Now that I can go paperless with Xournal, let's go back to productivity tweaks. One of the annoying thing on the thinkpad yoga was the default configuration for the touchpad. To tailor its behaviour to my liking I copied the file /etc/X11/xorg.conf.d/50-synaptics.conf and pasted it back with a higher precedence as 60-synaptics.conf. Then I copied most of the content from the original 50-xxxxx.conf and made some changes. Why not changing the content of 50-xxxxxx.conf outright? because with the next synaptics update the file will be reset. Now, what I changed was the order of the buttons:
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "PalmDetect" "1"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
        MatchDevicePath "/dev/input/event*"
EndSection
```This way, tapping with one finger is normal click, with 2 fingers is right-click and with 3 fingers is the third click. Seemed more natural to me. Although I set it, I dont know what the palmdetect option does?! Another section I modified in 60-synaptics.conf is the touchpad areas. Alala, what a nightmare in the begining when I couldnt click or eveytime I tapped the cursor would slip a few pixels from my target!! Now, the top 5% of the touchpad is inactive so I can rest my thumb beyond the touchpad red lines when using the track point. Same with the bottom edge, I deactivated the last 7% so the cursor doesnt slip when I try to do a right or middle click.
```
# This option enables the bottom right 40% to be a right button, the middle 20% a middle click and the rest of the clickpad a normal left click.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "60% 0 82% 0 40% 59% 82% 0"
#       To disable the bottom edge area so the buttons only work as buttons,
#       not for movement, set the AreaBottomEdge
    Option "AreaTopEdge" "5%"
    Option "AreaBottomEdge" "93%"
EndSection
```
With these basic modifications, my Manjaro setup is highly functional, with Xfce it is snappy, and with kwin it is beautiful!:P

At last, a few things arent working still. "xinput list" says I have an eraser...is that the red end of the pen? I haven't managed to get it working so far.  Also, what are the STMicro and Acer devices here? :
```
[gman@ThinkManjaro ~]$ lsusb
Bus 003 Device 004: ID 056a:00ec Wacom Co., Ltd 
Bus 003 Device 003: ID 0483:91d1 STMicroelectronics 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:029d Acer, Inc 
Bus 001 Device 003: ID 04f3:0254 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I strongly suspect STMicro to be the sensor hub that includes the accelerometer. Getting it working would mean automatic rotation of the screen...I'd like that! The Acer device must be doing something too but I havent found out yet. On another command I remember 2 devices where not recognised and I believe it was these 2; I just forgot what command I typed. Finally the screen hinges are supposed to send some signal past the 180degree as we enter tent mode and tablet mode; only I couldnt find out the way to get this signal.
Any help to get further hardware working would be greatly appreciated! :D 

But even as is, with the scripts in place, this machine is great! I love the way it feels, I love to touch it, I love its look and is mat finish, I love its performance. Last thing I want to say is, coming from a 13.3inch Dell XPS 13 laptop from 2008 with a resolution of 12xx*7xx, this 12.5inch screen with its great resolution feels large, bigger than my physically-bigger previous screen!

---

### Post by ZICODIAN on 2014-01-02
Inspired by djahma, I have put together a small, rough utility called spin that may be of use. I have tested it on my ThinkPad S1 Yoga with active digitiser.

[https://github.com/wdbm/spin](https://github.com/wdbm/spin)

---

### Post by mikewimmer on 2014-01-04
First of all, fantastic thread! Helped me already tremendously to get my laptop working well!

> **djahma said:**
> 
Finally the screen hinges are supposed to send some signal past the 180degree as we enter tent mode and tablet mode; only I couldnt find out the way to get this signal.
Any help to get further hardware working would be greatly appreciated! :D 


I think I can help with this issue: I figured out that there is an ACPI event triggered when the screen is completely folded to tablet mode (only when folded completely 360 degrees, unfortunately not after 180 degrees). 
Also, note that the same event is triggered when the laptop is folded to tablet mode, as well when it's folded back to laptop mode

One can use this ACPI event to run some script like. For this, one needs to put an event script into /etc/acpi/events:

```

# /etc/acpi/events/ibm-tabletmode
# This is called when the user completely flips the display and calls
# /etc/acpi/ibm-tabletmode.sh for further processing.

event=ibm/hotkey LEN0068:00 00000080 000060c0
action=/etc/acpi/ibm-tabletmode.sh

```

I wanted something simple, deactivate touchpad and touchscreen (I only want to use the pen in tablet mode), which I achieved with
this script as /etc/acpi/ibm-tabletmode.sh:

```

#! /bin/bash
# When converted to tablet, switch off touchpad and touchscreen
# Since opening and closing tabletmode is signaled by the same ACPI event,
# the script toggles the touchpad/touchscreen.

touchscreen=$(xinput list-props "ELAN Touchscreen" | grep "Device Enabled" | awk -F ":" '{print $2}')
touchpad=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | awk -F ":" '{print $2}')

if [ $touchscreen -eq 1 ]; then
    xinput --set-prop "ELAN Touchscreen" "Device Enabled" 0;
else
    xinput --set-prop "ELAN Touchscreen" "Device Enabled" 1;
fi

if [ $touchpad -eq 1 ]; then
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0;
else
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1;
fi

```

This script toggles touchpad/touchscreen (toggling is necessary as the folding/unfolding gives the same ACPI event.

Now, this is very simple, in principle it is also possible with a little more effort to trigger one of the more complicated scripts shown above.

I haven't made any progress with the accelerometer: older thinkpads cold use a kernel module named hdaps, but this does not seem to work on this machine.

One problem that I still have is that with the brightness keys, I can only change the brightness in 4 discrete steps, although the brightness bar shows more intermediate steps! Any ideas?

---

### Post by djahma on 2014-01-06
> **mikewimmer said:**
> 
One can use this ACPI event to run some script like. For this, one needs to put an event script into /etc/acpi/events:

```

# /etc/acpi/events/ibm-tabletmode
# This is called when the user completely flips the display and calls
# /etc/acpi/ibm-tabletmode.sh for further processing.

event=ibm/hotkey LEN0068:00 00000080 000060c0
action=/etc/acpi/ibm-tabletmode.sh

```

Thank you Mike! This trick is superb! 
How have you found out the correct hotkey to watch? Is there a way to see/read these hotkeys as they occur? We could go a lot further in integrating our hardware in our OS if we could discover them. Googling for a way to read them, some guy said to do "cat /proc/acpi/events"; unfortunately there is no such file in my system.

> One problem that I still have is that with the brightness keys, I can  only change the brightness in 4 discrete steps, although the brightness  bar shows more intermediate steps! Any ideas?
I've assigned a command in "application shortcuts" under xfce, in the keyboard settings: "xbacklight -dec 5%" for the XF86MonBrightnessDown key; and "xbacklight -inc 5%" for the XF86MonBrightnessUp key. I don't have the nice desktop visual anymore as I press these keys, but at least brightness is finely tuned now.

---

### Post by djahma on 2014-01-06
hmhm... Actually, I can't manage to get the /etc/acpi/events trick to work:oops: the script by itself works fine, its path in the events/file is correct, I copied pasted your code, the online literature says it is as simple as you wrote it...but it doesn't work on my side!
I discovered kacpimon along the way: there are many events we could plug to, expecially the 4 special keys above f9-f12 which do not work at the moment

---

### Post by mikewimmer on 2014-01-06
Hi djahma,

sorry about my premature enthusiasm - turn out it now also doesn't work for me as I figured out today. This is weird: As long as I run acpid in the foreground ( I ran "acpid -d -l" in order to debug the whole thing), it works, but if run as a daemon using /etc/init.d/acpid, irt doesn't. Furthermore, I don't find anything in the logs ,,, this needs some more debugging (but I'll be busy the next days).

As for the ACPI events, I found them using "acpi_listen" that was installed by defualt on my Ubuntu 13.10. You seem to have ACPI events for the buttons above f9-f12? I don't seem to get anything there.

As for the backlight issue, I figured out that there are two entries in /sys/class/backlight: acpi_video0 and intel_backlight. Writing (as root) a number like "echo 123 >/sys/class/backlight/intel_backlight/brightness" always works and changs the screen brightness. Writing a number to acpi_video0/brightness only has an effect for certain numbers (mostly those divisible by 10 or 5), for a  number inbetween nothing happens! Apparently gnome is using the acpi_video0 device, and hence I only see sometimes a brightness change, namely if gnome writes one of the "good" numbers there ...

---

### Post by djahma on 2014-01-08
> **mikewimmer said:**
> This is weird: As long as I run acpid in the foreground ( I ran "acpid -d -l" in order to debug the whole thing), it works, but if run as a daemon using /etc/init.d/acpid, irt doesn't. Furthermore, I don't find anything in the logs ,,, this needs some more debugging (but I'll be busy the next days).
As I found out on my Manjaro install, the default deamon is ktpacpid instead of acpid, therefore, the /etc/acpi/ folder is never screened. You probably have the same since it is a kernel thing (3.10 for me). I'll do more research on that later on.

---

### Post by ZICODIAN on 2014-01-08
Inspired by mikewimmer, I have added monitoring of the laptop/tablet usage configuration to the spin utility. So, the computer toggles between laptop and tablet modes when it detects the ACPI event associated with the screen being folded or unfolded.

An obvious limitation of this utility is that it makes the assumption that it was started with the computer in the laptop usage configuration as opposed to the tablet usage configuration. The ACPI event mentioned by mikewimmer appears not to specify the usage configuration, only that the configuration has changed. Is there some way to detect the current usage configuration?

Another limitation is the lack of monitoring of acceleration information. Is there a good way of monitoring this?

I welcome comments on spin.

[https://github.com/wdbm/spin](https://github.com/wdbm/spin)

---

### Post by mikewimmer on 2014-01-10
> **ZICODIAN said:**
> Inspired by mikewimmer, I have added monitoring of the laptop/tablet usage configuration to the spin utility. So, the computer toggles between laptop and tablet modes when it detects the ACPI event associated with the screen being folded or unfolded.

An obvious limitation of this utility is that it makes the assumption that it was started with the computer in the laptop usage configuration as opposed to the tablet usage configuration. The ACPI event mentioned by mikewimmer appears not to specify the usage configuration, only that the configuration has changed. Is there some way to detect the current usage configuration?

Another limitation is the lack of monitoring of acceleration information. Is there a good way of monitoring this?

I welcome comments on spin.

[https://github.com/wdbm/spin](https://github.com/wdbm/spin)

Oh, beautiful! The solution of listening to the socket of the acpi deamon is really neat.

Acceleration sensing would be extremely cool, but I suspect there's no kernel module for the sensor yet ...

---

### Post by djahma on 2014-01-11
Back with some answers!

First, Zicodian, that's a proper nerdy work you've put there! cheers for that.

Mike, I found out why the script from /etc/acpi was not running properly. But first, one needs to run acpid. On my system, systemd had it disabled by default; one can check that with "systemctl list-unit-files"; and then enable acpid at next reboot with "systemctl enable acpid". There from, events files will be parsed (all of them) in /etc/acpi/events every time an acpi event occurs. Once an event is matched, the corresponding action script is run...as "root".
Ok, but then, X programs such as xinput won't be run in our action scripts, because "root" is not allowed to connect to X by default since it doesn't have a .Xauthority file in its home folder... Long story short, add the following exports at the beginning of your scripts and it will work, here is your script amended Mike:
```
#!/bin/bash
# When converted to tablet, switch off touchpad
# Since opening and closing tabletmode is signaled by the same ACPI event,
# the script toggles the touchpad.

export XAUTHORITY=`ls -1 /home/*/.Xauthority | head -n 1`
export DISPLAY=":`ls -1 /tmp/.X11-unix/ | sed -e s/^X//g | head -n 1`"

touchpad=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | awk -F ":" '{print $2}')
if [ $touchpad -eq 1 ]; then
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
else
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
fi
```
Many thanks to Attila who posted [this]("http://askubuntu.com/questions/91534/disable-touchpad-while-the-lid-is-down")!

Any news on the STMicro sensor-hub? (for the accelerometer and light sensor)
What about the keys above F9-F12? Has anyone dared to rewrite the thinkpad_acpi driver to get them working? :D

---

### Post by djahma on 2014-01-11
Today I've been playing with multitouch, in the name of [touchegg]("https://code.google.com/p/touchegg/").
It worked right away with the touchscreen but not with the touchpad. So I had to install xf86-input-synaptics-mtpatch to make it work. Unfortunately, touchegg made the touchpad way too sensitive, it was unusable, and also, only 2 touches were recognised instead of 3 before that. So I returned to xf86-input-synaptics driver so that touchegg could only work with the touchscreen, and leave synaptics handle the touchpad.

I set touchegg as a startup program and played with its conf file in [/home/user/.config/touchegg/touchegg.conf]("http://pastebin.fr/32257") until I was happy. The result is FANTASTIQUE!

From touchegg wiki you can see the possibilities. It can handle up to 5 touches and trigger key combinations on any gesture (pinch is difficult to use though). Using kwin, I naturally associated gestures for the desktop grid and cube. It's just great navigation among windows and desktops in tablet mode now. Also scrolling was difficult before touchegg, I had to install an addon in firefox for example, but not any more, it scrolls everywhere! Our Thinkpad Yoga is a great machine to use this program. So today I jumped into a new dimension:cool:

I kind of gave up on implementing gestures on the touchpad due to the tech problems with the programs I tried (xswipe, easystroke, touchegg), but I am open to suggestions;-)

---

### Post by tthorb on 2014-01-14
I got mine Thinkpad Yoga (20CD0034MN) yesterday and installed Kubuntu 13.10. Most of the behaviour are very nice out of the box.
Thanks for a nice thread here!

Clickpad:

I have added a file for setting click behavour in xorg.conf.d. I used the settings from here: 
[http://forum.manjaro.org/index.php?topic=9671.0](http://forum.manjaro.org/index.php?topic=9671.0)
with the exception of SoftButtonAreas, which I have set like this:
        Option "SoftButtonAreas" "60% 0 0 82% 40% 59% 0 82%"

Wacom Pressure Sensibility:

This is working, but on light pressure in inkscape and krita, the lines thickness gets wiggly. I have played with PressureCurve, Threshold, RawSample and Suppress through synclient, but have not found a good solution.
In xournal, the pressure sensitivity works well out of the box.

Multitouch (touchscreen):

For plasma widgets, multitouch works out of the box. But for adding multitouch behavour to kwin windows, the only solution I found was using touchegg. This seem to be working fine, but the movement of kwin windows are lagging when using this.

Accelerometer and rotation:

I have not looked deep into this matter, but I look forward to a solution for auto-rotation of the screen. Also tp-theft would be fun. Spin-scripts will do for now.

Touchscreen-friendly themes or working plasma-active?

I tried kubuntu-active without any success. I had to remove it to get the mouse icon back. Have others tried out more touchscreen friendly themes or tested out plasma-active?

All in all - this machine has proved to be working very well with kubuntu! 

Does not work out of the box:
- Clickpad right and middle click - see link above for solution
- Autorotate - have not found a solution

Everything I expect from a normal laptop, like sleep, brightness buttons, wifi etc worked out of the box in kubuntu. I am very satisfied!

---

### Post by djahma on 2014-01-14
> **tthorb said:**
> 
Does not work out of the box:
- Clickpad right and middle click - see link above for solution
- Autorotate - have not found a solution

Everything I expect from a normal laptop, like sleep, brightness buttons, wifi etc worked out of the box in kubuntu. I am very satisfied!
Hey tthorb, does that imply the icon keys above F9-F12 work in Kubuntu?
What about hibernate mode? do you get your programs back when you switch back on?
Regarding autorotate, I've just spent an hour trying to find out which device is 0483:91D1... 0483 is STMicro vendor and they have plenty of linux drivers for their sensors. The most accurate info I got was [this list]("http://www.linux-usb.org/usb.ids"), but no 91D1:-(

---

### Post by Sheldor on 2014-01-14
@ [**[COLOR=#000000]jon_mease[/COLOR]**]("http://ubuntuforums.org/member.php?u=352816")
Sorry for the late reply, i sent mine back, and planing to buy an Thinkpad x240 (with full hd display), i don't realy need the touchpad. I would be a "nice to have" but if it*s not properly supported by ubuntu, i am fine without it

---

### Post by tthorb on 2014-01-15
> does that imply the icon keys above F9-F12 work in Kubuntu?

They are not set up and have not a keycode, but is recognized when running acpi_listen.

It seems quite easy to set up events with these keys:
[http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads](http://askubuntu.com/questions/125367/enabling-mic-mute-button-and-light-on-lenovo-thinkpads)

But I really don't see the point of these keys, so I don't think I will do something with this.

> What about hibernate mode? do you get your programs back when you switch back on?

I have not set up a swap partition (yet), so I will not try this (for now).

(Hibernate is disabled out of the box in newer *buntus: [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html))

> Regarding autorotate, I've just spent an hour trying to find out which device is 0483:91D1... 0483 is STMicro vendor and they have plenty of linux drivers for their sensors. The most accurate info I got was [this list]("http://www.linux-usb.org/usb.ids"), but no 91D1:-(

Interesting!

---

### Post by djahma on 2014-01-18
Back on autorotation, the guy from hid_sensor_hub module said it required iio for the sensors to register. And indeed, within iio tree, the kernel has specific modules for STMicro sensors. However, after compiling kernel 3.10.27 with the whole lot enabled, I still can't see any device under /sys/bus/iio/devices; meaning the sensor hub is still not managed properly.
I went beyond my linux skills limit to do that, that's why I really hope someone more knowledgeable about this stuff could pick up that trail;)

---

### Post by adam29 on 2014-01-18
Hi guys, thanks for this thread :)

I testing Thinkpad Yoga on Ubuntu 13.10., but had little battery life. Only 2-4 hours for office work.

What is your real battery live?

---

### Post by djahma on 2014-01-19
> **adam29 said:**
> 
What is your real battery live?

I just played for almost 3 hours with genymotion (virtualbox based android machine) with an external drive plugged in most of the time, wifi aerial on, firefox and thunderbird running: my battery indicator shows 51% remaining. I'm on Manjaro Xfce with kwin window manager..

---

### Post by tthorb on 2014-01-21
> **mikewimmer said:**
> Hi djahma,

sorry about my premature enthusiasm - turn out it now also doesn't work for me as I figured out today. This is weird: As long as I run acpid in the foreground ( I ran "acpid -d -l" in order to debug the whole thing), it works, but if run as a daemon using /etc/init.d/acpid, irt doesn't. Furthermore, I don't find anything in the logs ,,, this needs some more debugging (but I'll be busy the next days).


Did not test this until today. When the script is called by an acpi event, it does not have access to the active users X. You need to set XAUTHORITY and DISPLAY in the script. An easy fix : [https://github.com/rephorm/xuserrun](https://github.com/rephorm/xuserrun)

---

### Post by tthorb on 2014-01-21
And by the way... I change windows button to F20 when going in tablet-mode, (xmodmap -e 'keycode 133 = F20' and xmodmap -e 'keycode 133 = Super_L') - and in I have bound F20 to show (kde plasma) dashboard.

---

### Post by ZICODIAN on 2014-02-01
Have any of you had any success in getting the TrackPoint pointing stick with the clickpad to behave as a scroll wheel?

When I use a TrackPoint with dedicated buttons (by this I mean pressing dedicated TrackPoint button 2 and moving the TrackPoint up or down and so on), the ```xev``` output indicates that button 4 is recognised as a scroll up operation and button 5 is recognised as a scroll down operation. The ```xev``` output for the scroll wheel of a typical mouse indicates the same. However, when I use a TrackPoint with the clickpad of the ThinkPad Yoga, the buttons 4 and 5 are not registered, with instead button 2 showing up in isolation. How can I get the button 2-TrackPoint motion combination to exhibit the scrolling behaviour?

There's been some discussion on the issue here [https://bbs.archlinux.org/viewtopic.php?pid=1359126](https://bbs.archlinux.org/viewtopic.php?pid=1359126), but I have not been successful in implementing the ideas expressed there.

---

### Post by Garrone on 2014-02-05
Hello, 
On the lenovo website they propose at the same prise "ClickPad whith antena and Module" and "Clickpad without antena and Module", default is without, I want to select the one with NFC but I am afaid that it could be less suported that the regular one... Acording to you guys whitch should I chose ? 
Other question, does any one atempted/managed to dual boot with windows 8.1 ? 
And what about the mSATA of 16gb ? Is it totaly usless as soon a we modifie the initial configs or is it posible to configure windows and Linux to use it eficently ?
Thx for your attention and please forgive my bad english .

---

### Post by Garrone on 2014-02-06
I think [this]("http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together") treat solved the dualboot problem that I haven't yet. :o

---

### Post by tiekei2 on 2014-02-10
> **adam29 said:**
> Hi guys, thanks for this thread :)

I testing Thinkpad Yoga on Ubuntu 13.10., but had little battery life. Only 2-4 hours for office work.

What is your real battery live?

same problem here (Ubuntu 13.10 (3.11.0-15), Debian Jessie), I read a lot about acpi and thinkpad-acpi, but I found no solution to the lowered battery life yet. As it looks, the battery is not really supported:
```

$ sudo acpi -V
Battery 0: Discharging, 4%, 00:11:25 remaining
Battery 0: design capacity 3317 mAh, last full capacity 3445 mAh = 100%
Adapter 0: off-line
[...]

```

---

### Post by dude-mail on 2014-02-26
Hi, I'm new to ubuntu and i want to know how can i use  your PenInOut.sh script on my Yoga?
I have made a knew file, pasted the code and made a executable with chmod +x.
 Thanks :)

---

### Post by djahma on 2014-02-27
> **dude-mail said:**
> I have made a knew file, pasted the code and made a executable with chmod +x.
 Thanks :)

At this stage, you're set dude. Doesn't it work when you run that script? (the touchscreen should be disabled when the pen is in proximity)

BTW, I posted a few things for the Yoga [here]("http://forum.manjaro.org/index.php?topic=9671"). (I've been hopping from one distro to the next for a while so details may differ with Kubuntu)

---

### Post by pfpschneider on 2014-03-06
> **djahma said:**
> Back on autorotation, the guy from hid_sensor_hub module said it required iio for the sensors to register. And indeed, within iio tree, the kernel has specific modules for STMicro sensors. However, after compiling kernel 3.10.27 with the whole lot enabled, I still can't see any device under /sys/bus/iio/devices; meaning the sensor hub is still not managed properly.
I went beyond my linux skills limit to do that, that's why I really hope someone more knowledgeable about this stuff could pick up that trail;)

I put together some autorotation code for the Yoga 2 Pro, which might be similar to the Thinkpad Yoga.  I also have patched drivers, again for the Yoga 2 Pro, but the Thinkpad Yoga may be similar.

You need both the sensor hub and the IIO modules to be included in your kernel modules.

---

### Post by ristopekkala on 2014-03-08
I'm having a strange reset of pointer position when trying to play Urban Terror and Americas Army. It is only with the mouse this happens. All other devices like TouchPad and Wacom behaves the same. In some fixed time intervals the view jumps back to earlier position making looking around or moving in circles impossible. Should I disable some device before playing? 

/ Risto

---

### Post by Ray-Ven on 2014-03-28
Hello,

I'm using an Yoga Thinkpad as well, mine comes with an elan touchscreen and wacom pen. could you manage to get multitouch on screen? Mine is just singletouch.

And is there some success with autorotation? Spin works like a charm, but I'd prefer some automation.

I have to mention that I'm working with kubuntu trusty!

Thanks

Ray

---

### Post by Ray-Ven on 2014-03-28
This is how I use my touchpad to make it work with the trackpoint:
```

#!/bin/bash
TOUCHPAD="SynPS/2 Synaptics TouchPad"
TRACKPOINT="TPPS/2 IBM TrackPoint"
echo "setting right area of pad to rightclick. Order:  RightButtonAreaLeft, RightButtonAreaRight, RightButtonAreaTop, RightButtonAreaBottom, MiddleButtonAreaLeft, MiddleButtonAreaRight, MitddleButtonAreaTop, MiddleButtonAreaBottom"
xinput set-prop "${TOUCHPAD}" "Synaptics Soft Button Areas" 4000, 0, 0, 4466, 3000, 3999, 0, 1400

echo "enable twofingerscrolling in both directions"
xinput set-prop "${TOUCHPAD}" "Synaptics Two-Finger Scrolling" 1, 1

echo "shortening upper edge to reserve space for 'just button' actions. Order: left, right, top, bottom"
xinput set-prop "${TOUCHPAD}" "Synaptics Area" 0, 0, 1500, 0

echo "enabling palm detection"
xinput set-prop "${TOUCHPAD}" "Synaptics Palm Detection" 1

echo "Middle mouse button emulation for scrolling on trackpoint"
xinput set-prop "${TRACKPOINT}" "Evdev Wheel Emulation" 1
xinput set-prop "${TRACKPOINT}" "Evdev Wheel Emulation Button" 2 
xinput set-prop "${TRACKPOINT}" "Evdev Wheel Emulation Timeout" 200
xinput set-prop "${TRACKPOINT}" "Evdev Wheel Emulation Axes" 6 7 4 5 # horizontal und vertikal

echo"enable tap events"
xinput set-prop "${TOUCHPAD}" "Synaptics Tap Action" 2, 3, 1, 1, 1, 3, 0

echo "touchpad on"

xinput set-prop "${TOUCHPAD}" "Synaptics Off" 0

echo "list actual properties"
xinput list-props "${TOUCHPAD}" 

echo "no touch while typing"
syndaemon -i 0.5 -d

```

I'm using synaptics driver 1.7.99.1 which is supposed to work better with newer Lenovos... I don't feel any differences though.

If you don't use the touchpad as a touchpad, just configure it as a scrollpad (only for scrolling and clicking, no moving the cursor). It would even be possible to do this: if "middletouchpadbutton is pressed" --> "Touchpad is just for scrolling" else "Touchpad is used as a touchpad", as middlemousebutton of the touchpad sends an seperate event (seen in xev). You'd have to keep the pad pressed though

[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683"]Here are some strange patches to make middle-mouse-button-scrolling work
[/URL]

---

### Post by tvantalon on 2014-04-01
Hi djahma, 
I am also trying to make the accelerometer work. You seem more advanced than me. Have you downloaded the driver from [SIZE=2]STMicroelectronics[/SIZE]? Do you know which module is inside the yoga?

Thank you

---

### Post by djahma on 2014-04-04
> **tvantalon said:**
> Hi djahma, 
I am also trying to make the accelerometer work. You seem more advanced than me. Have you downloaded the driver from [SIZE=2]STMicroelectronics[/SIZE]? Do you know which module is inside the yoga?

Thank you

I havent spent any more time on this matter actually. Like** pfpschneider ** said above, the way forward is pretty much to compile your kernel with iio (in tree and not as a module I was told, but I couldn't get it to work anyway, so I'm probably wrong). Then, hid_sensor_hub module should be able to handle the accelerometer... That's why I glimpse at this thread any now and then: I hope someone could come up with an easy solution.

On a different subject, has anyone managed to get the clickpad working with touchegg? what about getting the "pinch in" gesture recognised on touchscreen/clickpad (whichever)?

---

### Post by ZICODIAN on 2014-04-05
Hi *

The problem of wheel emulation scrolling using the TrackPoint with the clickpad is solved. A driver ([https://aur.archlinux.org/packages/xf86-input-evdev-trackpoint/](https://aur.archlinux.org/packages/xf86-input-evdev-trackpoint/)) for Arch was created by Taegil Bae (esrevinu) ([https://bitbucket.org/esrevinu/xf86-input-evdev-trackpoint](https://bitbucket.org/esrevinu/xf86-input-evdev-trackpoint)) and a procedure ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/40](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/40)) was described by dalcde ([https://launchpad.net/~dalcde](https://launchpad.net/~dalcde)) for packaging the driver for Ubuntu and updating. The procedure is as follows:

```

    sudo apt-get install git
    sudo apt-get build-dep xserver-xorg-input-evdev xserver-xorg-input-synaptics
    
    wget https://aur.archlinux.org/packages/xf/xf86-input-evdev-trackpoint/xf86-input-evdev-trackpoint.tar.gz
    tar -xzf xf86-input-evdev-trackpoint.tar.gz
    git clone git://git.debian.org/git/pkg-xorg/driver/xserver-xorg-input-evdev
    git clone git://git.debian.org/git/pkg-xorg/driver/xserver-xorg-input-synaptics
    
    mv xf86-input-evdev-trackpoint arch
    mv xserver-xorg-input-evdev evdev
    mv xserver-xorg-input-synaptics synaptics
    
    cp synaptics/src/{eventcomm.c,eventcomm.h,properties.c,synaptics.c,synapticsstr.h,synproto.c,synproto.h} evdev/src
    cp synaptics/include/synaptics-properties.h evdev/src
    cp arch/*.patch evdev
    
    cd evdev
    patch -p1 -i 0001-implement-trackpoint-wheel-emulation.patch
    patch -p1 -i 0008-disable-clickpad_guess_clickfingers.patch
    patch -p1 -i 0010-add-synatics-files-into-Makefile.am.patch
    
    dpkg-buildpackage
    
    cd ..
    sudo dpkg -i xserver-xorg-input-evdev_*.deb
    sudo apt-get remove xserver-xorg-input-synaptics
    
    sudo mkdir /etc/X11/xorg.conf.d/
    sudo cp arch/90-evdev-trackpoint.conf /etc/X11/xorg.conf.d

```

I confirm that this works well.

---

### Post by tvantalon on 2014-04-06
[COLOR=#000000][FONT=Sans Serif]Thank you for you indication, I will see if I can find time to try that.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]> **djahma said:**
>  what about getting the "pinch in" gesture recognized on touchscreen/clickpad (whichever)?[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]I  do not exactly now the situation under Ubuntu ( I am an undercover  archlinux user), but it seems that touchegg use Synaptics driver. [/FONT][/COLOR]Unfortunately,  the touch screen can use either the Wacom driver or the evdev one.  Touchegg do not support the Wacom driver (at least on my archlinux) and have a partial support for  the evdev one. I am afraid the "good thing to do" would be to hack Touchegg or its dependency to add support for the Wacom driver.

It seems Touchegg supported older Wacom driver (last section)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)
So maybe you can try to down grad the driver, add the parameter Gesture off to your x11 configuration.

---

### Post by tvantalon on 2014-04-06
Small update regarding the accelerometer.  (I did it in archlinux, but the procedure should be the same for ubuntu). I compiled a kernel and enabled the accelerometer, magnetometer and gyroscop drivers. The drivers are in  "Device Drivers -> Industrial I/O support (IIO [=y])" (I enabled the HID and STMicroelectronics drivers). Now I have 3 new device in "/sys/bus/iio/devices".

---

### Post by pfpschneider on 2014-04-07
This code is available from [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop)

> **pfpschneider said:**
> I put together some autorotation code for the Yoga 2 Pro, which might be similar to the Thinkpad Yoga.  I also have patched drivers, again for the Yoga 2 Pro, but the Thinkpad Yoga may be similar.

You need both the sensor hub and the IIO modules to be included in your kernel modules.

---

### Post by metnix on 2014-04-08
*edit: With the release of 14.04, kernel version 3.13 is default which provides a better solution, see below*

Hi guys,

I made a workaround for adjusting the backlight level by changing the kernel boot options.
(Note: it's usually worth pointing out that you should always backup system files before messing around, it's a bit annoying when a typo renders your system unbootable)
(Note2: I'm running the Unity desktop not KDE, but this stuff should be independent of desktop)

**What works:**
Setting brightness levels in small increments

**What doesn't work:**
[s]The brightness indicator (jumps around a bit, it's probably still using the acpi_video0?)[/s] *edit: works like a charm!*

[B]1. Test the new options without any persistent changes[INDENT]
[/INDENT]
[/B][INDENT]If you're on a single boot system (like me) you probably have to enable the grub menu first.
Open /etc/default/grub for editing, comment out the line beginning with "GRUB_HIDDEN_TIMEOUT" like so:
> # GRUB_HIDDEN_TIMEOUT=0
Then update your GRUB:
> sudo update-grub

**Reboot to GRUB**
At the GRUB menu select the default entry and press 'e' for edit, and add [s]"acpi_osi=Linux acpi_backlight=vendor"[/s] "video.use_native_backlight=1" to the end of the line beginning with linux, e.g.:
> 
setparams 'Ubuntu'

recordfail[INDENT]
load_video
gfxmode $linux_gfx_mode
insmod gzip
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then[INDENT]
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=achi0,msdos5 0b0887f9-5aab-4ae5-8109-1458a79c3692
[/INDENT]
else[INDENT]
search --no-floppy --fs-uuid --set=root 0b0887f9-5aab-4ae5-8109-1458a79c3692
[/INDENT]
fi
[s]linux /boot/vmlinuz-3.11.0-18-generic root=UUID=0b0887f9-5aab-4ae5-8109-1458a79c3692 ro quiet splash $bt_handoff acpi_osi=Linux acpi_backlight=vendor[/s]
linux /boot/vmlinuz-3.11.0-18-generic root=UUID=0b0887f9-5aab-4ae5-8109-1458a79c3692 ro quiet splash $bt_handoff **video.use_native_backlight=1**
initrd /boot/initrd.img-3.11.0-18-generic
[/INDENT]

press <F10> to boot.
When your systems is up try out the brightness up/down keys, it should now work as expected. If it does, proceed to...
[/INDENT]

**2. Make persistent changes in GRUB defaults**[INDENT]
Open /etc/default/grub for editing, add [s]"acpi_osi=Linux acpi_backlight=vendor"[/s] "video.use_native_backlight=1" to the line beginning with "GRUB_CMDLINE_LINUX", e.g.:
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[s]GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"[/s]
GRUB_CMDLINE_LINUX=**"video.use_native_backlight=1"**

...

(optionally, if you're on a single boot system, you can uncomment GRUB_HIDDEN_TIMEOUT=0 again)
Update your GRUB:
> sudo update-grub

**Reboot**
That's it!
You should now have nice persistent backlight controls!



[/INDENT]
Some credit:
The [ARCH wiki]("https://wiki.archlinux.org/index.php/backlight") was helpful

BTW, this thread has been of great use for me with setting up my system, thanks a lot!

---

### Post by Ottoko on 2014-04-10
I recently bought Lenovo TPY and this thread has been a great help setting up things! Script with patches for clickpad is great, I haven't tried the spin scripts yet but just wanted to say thank you :)

---

### Post by Ottoko on 2014-04-17
I had issues with the power consumption... My battery only lasted few hours with 14.04 beta. The latest 3.15-rc1 kernel has lots of intel fixes so I applied that. The biggest issue was that ondemand kernel cpu governor did not work as expected. I changed governor to powersave and now my idle clocks are 800MHz and during video transcoding CPU cores went to 3.0GHZ (i7 U4500). 

I'm also using the spin script and the middle scroll patch script and I think the TPY experience is quite good now.

---

### Post by Ray-Ven on 2014-04-21
Hey there,

is there any way to get multitouch (touchscreen) working? Any help would be apreciated!

Thanks
Ray

---

### Post by Ray-Ven on 2014-04-21
wasn't aware of touchegg :-) niiiiiice! Multitouch works like a charm (14.04)...

but... 2 finger pinch actions (zoom) don't work.... Does it work for you?

Thanks,
Ray

---

### Post by nomailing on 2014-05-03
> **Ottoko said:**
> I had issues with the power consumption... My battery only lasted few hours with 14.04 beta. The latest 3.15-rc1 kernel has lots of intel fixes so I applied that. The biggest issue was that ondemand kernel cpu governor did not work as expected. I changed governor to powersave and now my idle clocks are 800MHz and during video transcoding CPU cores went to 3.0GHZ (i7 U4500). 

[COLOR=#000000]I also have the Yoga with the i7-U4500, but [/COLOR]I am running ubuntu 14.04 with kernel 3.13.0.24. For me ondemand seems to work as expected.
Here are the cpu frequencies reported by turbostat (cpuinfo seems to not report the correct values):[FONT=arial]

[/FONT][TABLE="width: 500"]
[TR]
[TD]governor[/TD]
[TD]idle cpu freq [GHz][/TD]
[TD]full load cpu freq [GHz][/TD]
[/TR]
[TR]
[TD][FONT=arial]ondemand[/FONT][/TD]
[TD]0.8[/TD]
[TD]2.7 drops to ~2.1 after few sec[/TD]
[/TR]
[TR]
[TD][FONT=arial]powersave[/FONT][/TD]
[TD]0.8[/TD]
[TD]0.8[/TD]
[/TR]
[TR]
[TD][FONT=arial]performance[/FONT][/TD]
[TD]1.8[/TD]
[TD]2.7 drops to ~2.1 after few sec[/TD]
[/TR]
[/TABLE]

Is there a setting to allow frequencies up to 3 GHz (I think that is the max Turbo Boost frequency) in kernel 3.13? 
Or do you suggest upgrading the kernel to 3.15 to get the full performance?
Or does the kernel update only improve battery consumption?

---

### Post by IzRey on 2014-05-28
Thanks everyone for your help. This thread has been very useful.

I am using spin and have modified the grub file to fix the brightness adjustments.

I am still experimenting with touchegg, and will be sure to give updates if I find anything worth sharing.

Also, extremely interested in getting accelerometer working will try to get my hands dirty with that.

Thanks again!!

---

### Post by stefano15 on 2014-05-30
> **Ottoko said:**
> I had issues with the power consumption... My battery only lasted few hours with 14.04 beta. The latest 3.15-rc1 kernel has lots of intel fixes so I applied that. The biggest issue was that ondemand kernel cpu governor did not work as expected. I changed governor to powersave and now my idle clocks are 800MHz and during video transcoding CPU cores went to 3.0GHZ (i7 U4500). 

I'm also using the spin script and the middle scroll patch script and I think the TPY experience is quite good now.
Hi
Did 3.15-rc1 make any difference?
I am using (on Gentoo Linux - not Ubuntu) 3.14 and as I wrote [here]("http://www.blah-blah.ch/it/hardware/notebook-lenovo-yoga-s240/#battery") the battery lasts for ~7hrs (7 is more worst-case under normal usage. 7.5 to 8 would be more appropriate if you're just typing stuff or browsing simple pages like the ones of Wikipedia).
I am currently using Enlightenment (e16) but had the same runtimes when using the 3D-desktop Compiz + Emerald.
I am using the "Intel P state control" scheduler for the CPU (the most obvious impact of using it is the missing directory "/sys/devices/system/cpu/cpu0/cpufreq/**stats**") with the "ondemand" governor - not sure if it's better than the classical ACPI governor (especially after reading [this]("http://www.phoronix.com/scan.php?page=article&item=intel_pstate_linux315&num=1")).
I tried using PSR (Intel i915 module parameter "enable_psr=1" to enable the refresh of the eDP display only when there is something ro refresh) and yes, in my case it saved 1W out of the 7W total but it made screen refreshes unreliable (small refreshes like the ones of the console worked only intermittently and could force a refresh only by moving the mouse/pointer).

Thanks a lot for all the hints and the scripts!!! They were very useful.

Question:
As I have mentioned [here]("http://www.blah-blah.ch/it/hardware/notebook-lenovo-yoga-s240/#wireless") the only problem I have is that my wireless connection crashes from time to time (can be 20min, can be 8hrs...) and that the only way to make it work is to unload and reload all modules that have something to do with wireless => am I the only one experiencing this?
I have just started testing it with bluetooth and other stuff disabled.

Cheers

---

### Post by Ottoko on 2014-06-22
I switched back from .14 and .15 kernels to 3.13.0-29-generic (currently delivered in 12.04) and it seems that powersave works fine (cpu clocks goes to 800MHz on idle and power consumption seems to be in the same level as in .14 and .15 kernels).

The script for ClickPad doesn't work anymore (patches cannot be applied, I guess they are already integrated). Removed all settigns that script made but clickpad doesn't work at all on current default 14.04. Anyone running the latest 14.04 with middle click scrolling working?

---

### Post by mister-walter on 2014-08-21
> **ZICODIAN said:**
> Hi *

The problem of wheel emulation scrolling using the TrackPoint with the clickpad is solved. A driver ([https://aur.archlinux.org/packages/xf86-input-evdev-trackpoint/](https://aur.archlinux.org/packages/xf86-input-evdev-trackpoint/)) for Arch was created by Taegil Bae (esrevinu) ([https://bitbucket.org/esrevinu/xf86-input-evdev-trackpoint](https://bitbucket.org/esrevinu/xf86-input-evdev-trackpoint)) and a procedure ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/40](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/40)) was described by dalcde ([https://launchpad.net/~dalcde](https://launchpad.net/~dalcde)) for packaging the driver for Ubuntu and updating. The procedure is as follows:

```

    sudo apt-get install git
    sudo apt-get build-dep xserver-xorg-input-evdev xserver-xorg-input-synaptics
    
    wget https://aur.archlinux.org/packages/xf/xf86-input-evdev-trackpoint/xf86-input-evdev-trackpoint.tar.gz
    tar -xzf xf86-input-evdev-trackpoint.tar.gz
    git clone git://git.debian.org/git/pkg-xorg/driver/xserver-xorg-input-evdev
    git clone git://git.debian.org/git/pkg-xorg/driver/xserver-xorg-input-synaptics
    
    mv xf86-input-evdev-trackpoint arch
    mv xserver-xorg-input-evdev evdev
    mv xserver-xorg-input-synaptics synaptics
    
    cp synaptics/src/{eventcomm.c,eventcomm.h,properties.c,synaptics.c,synapticsstr.h,synproto.c,synproto.h} evdev/src
    cp synaptics/include/synaptics-properties.h evdev/src
    cp arch/*.patch evdev
    
    cd evdev
    patch -p1 -i 0001-implement-trackpoint-wheel-emulation.patch
    patch -p1 -i 0008-disable-clickpad_guess_clickfingers.patch
    patch -p1 -i 0010-add-synatics-files-into-Makefile.am.patch
    
    dpkg-buildpackage
    
    cd ..
    sudo dpkg -i xserver-xorg-input-evdev_*.deb
    sudo apt-get remove xserver-xorg-input-synaptics
    
    sudo mkdir /etc/X11/xorg.conf.d/
    sudo cp arch/90-evdev-trackpoint.conf /etc/X11/xorg.conf.d

```

I confirm that this works well.

I couldn't get these instructions to work (things have changed I suppose), but a user posted an updated installation script on the Launchpad bug page ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683))

---

### Post by Ottoko on 2014-08-21
Thanks for the post mister-walter.

I tried the script and it works well on my Thinkpad Yoga on 14.04.

1. Enable software sources: [http://askubuntu.com/questions/158871/how-do-i-enable-the-source-code-repositories](http://askubuntu.com/questions/158871/how-do-i-enable-the-source-code-repositories)
2. Execute script:

```
#!/bin/bash

sudo apt-get install libevdev-dev libevdev2
sudo apt-get build-dep xserver-xorg-input-evdev xserver-xorg-input-synaptics

wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0.orig.tar.gz)
wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0-1ubuntu1.diff.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0-1ubuntu1.diff.gz)
wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0-1ubuntu1.dsc](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-evdev_2.9.0-1ubuntu1.dsc)

wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0.orig.tar.gz)
wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0-1~exp2ubuntu2.diff.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0-1~exp2ubuntu2.diff.gz)
wget [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0-1~exp2ubuntu2.dsc](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.8.0-1~exp2ubuntu2.dsc)

dpkg-source -x --no-check xserver-xorg-input-evdev_2.9.0-1ubuntu1.dsc
dpkg-source -x --no-check xserver-xorg-input-synaptics_1.8.0-1~exp2ubuntu2.dsc

wget [https://aur.archlinux.org/packages/xf/xf86-input-evdev-trackpoint/xf86-input-evdev-trackpoint.tar.gz](https://aur.archlinux.org/packages/xf/xf86-input-evdev-trackpoint/xf86-input-evdev-trackpoint.tar.gz)

tar -xzf xf86-input-evdev-trackpoint.tar.gz

mv xf86-input-evdev-trackpoint arch
mv xserver-xorg-input-evdev-2.9.0 evdev
mv xserver-xorg-input-synaptics-1.8.0 synaptics

cp synaptics/src/{eventcomm.c,eventcomm.h,properties.c,synaptics.c,synapticsstr.h,synproto.c,synproto.h} evdev/src
cp synaptics/include/synaptics-properties.h evdev/src
cp arch/*.patch evdev

cd evdev
patch -p1 -i 0001-implement-trackpoint-wheel-emulation.patch
patch -p1 -i 0004-disable-clickpad_guess_clickfingers.patch
patch -p1 -i 0006-add-synatics-files-into-Makefile.am.patch

dpkg-buildpackage

cd ..
sudo dpkg -i xserver-xorg-input-evdev_*.deb
sudo apt-get remove xserver-xorg-input-synaptics

sudo mkdir /etc/X11/xorg.conf.d/
sudo cp arch/90-evdev-trackpoint.conf /etc/X11/xorg.conf.d

echo If everything was OK, than logout/reboot and enjoy fully working ThinkPad Trackpoint/ClickPad
echo If you want to deactivate touch area of ClickPad for pure TrackPoint usage
echo edit /etc/X11/xorg.conf.d/90-evdev-trackpoint.conf and change "0" to "1" at line
echo Option "AreaBottomEdge" "0"
```

Works very well. The palm detection is not enabled and that would be next thing to consider.

---

### Post by Ottoko on 2014-08-21
Has anyone figured out how to configure touchegg for touch screen for tablet use?

---

### Post by ognjen-maric on 2014-09-26
If anybody is still interested, I've put together a small package for Arch Linux to automatically rotate the screen when put into/out of tablet mode. I imagine it should work in Ubuntu without any changes, read the "docs":

[https://github.com/oggy-/thinkpad-yoga-rotate](https://github.com/oggy-/thinkpad-yoga-rotate)

---

### Post by xt-gr79 on 2014-09-27
Hi, thanks for sharing your package.
I' ve got a couple of questions
1) You say "whenput into laptop mode". Do you meen "tablet mode"? It makes more sence.
2) Itried it both in Ubuntu 14.04 (unity) and antergos linux. It didn't work (i've installed dependences, rebooted). Is there anything more to do?
I have my yoga since April and i'm still trying to make some things work (screen rotation, buttery consumption, gestures). I know there are mentioned some solutions in the forums but they either require some skills i dont' have, or they do not work properly...
Is there the posibility that someone makes a re-distribution especially for yogas?

---

### Post by ognjen-maric on 2014-09-27
> **xt-gr79 said:**
> 
1) You say "whenput into laptop mode". Do you meen "tablet mode"? It makes more sence.


Indeed, thanks for spotting that. I've edited my post to correct this.

> **xt-gr79 said:**
> 
2) Itried it both in Ubuntu 14.04 (unity) and antergos linux. It didn't work (i've installed dependences, rebooted). Is there anything more to do?


Yes, my instructions were incomplete. You also need to ```
chmod +x /etc/acpi/actions/rotate-screen.sh
``` If you're using Antergos (that's what I'm running), and have an AUR-aware package manager (e.g. yaourt), you can also just install thinkpad-yoga-rotate from AUR (I've updated that as well to fix the permissions). If you already have a copy of the script in /etc/acpi, you'll need to delete it first for the package to install. 

If it still doesn't work, let me know.

---

### Post by xt-gr79 on 2014-09-27
I installed it from AUR (used Pacmanxg), rebooted but there was no result...
I've tried it twice. Any thoughts?

---

### Post by ognjen-maric on 2014-09-28
I'm guessing it's one or both of the followingwi

1. you're using GNOME and the script didn't work with GNOME (I had only tested it with KDE and Xfce). Now it should work there as well, the new version is up on AUR.
2. maybe the acpid is not actually running - the service doesn't get enabled automatically when installed. Run "systemctl enable acpid.service; systemctl start acpid.service".

BTW there shouldn't be any need to reboot the computer.

---

### Post by xt-gr79 on 2014-09-28
Ok, thanks for the reply. 
No 1 was not correct, I used kde with antergos. However, No 2 worked. So it seems it was acpid.
The result was that the screen rotated 90 degrees as soon as the tablet mode was the active one. It keeps in that orientation even if i rotate the tablet. Is this that it is supposed to be? Or is it supposed to rotate along with the tablet?

---

### Post by ognjen-maric on 2014-09-29
The script doesn't rotate the scrren with the tablet, I don't know how to get the sensor data to do this; the current script relies on a simple ACPI event which is only triggered when switching to/from the tablet mode.

---

### Post by xt-gr79 on 2014-09-29
Ok, then. Thank you very much for the script. If you have any other solutions, please share them with us.

---

### Post by backman on 2014-10-20
What is the current status?

I installed 14.04 on thinkpad yoga and want to know if anyone and how got multitouch with full clickpad/trackpad working on unity. Also are thinkpad-acpi working? And which script works for autorotate? 

Thanks in advance

---

### Post by ragtag on 2015-01-06
Is there still a pressure issue with the Wacom pen in Krita and Inkscape, that tthorb mentions on around page 3 of this thread.

I'm considering getting this laptop for drawing, and need accurate and reliable pressure to work in Gimp, Krita and MyPaint.

---

### Post by cheflo on 2015-03-25
Thanks everyone who has posted advice for improving the Linux experience on the TP Yoga. I just got the 2nd generation of this machine and collected what modifications worked for me in a [new thread.]("http://ubuntuforums.org/showthread.php?t=2270774") Please contribute tips and tricks if you have any!

---

### Post by ZICODIAN on 2015-04-29
Hi *

I have added acceleration control to spin. [https://github.com/wdbm/spin](https://github.com/wdbm/spin)

---

### Post by mueller.pascal on 2015-09-02
Hi,

Just wanted to ask if there is a overview about the best scripts and everything? I'm currently digging myself through the thread and everything.

I wanted to add that I'm using the Pro Dock:
Dual Screen works
LAN works
USB Works
Shut Down and Start Button Works,
Never tried the HDMI, Im using DVI.

So basically: Pro Dock works, but it's stil lvery untested.

---

### Post by mueller.pascal on 2015-09-02
How can I add:
-Scrolling with one finger (currently only works with 2 - and feels odd) - on the screen
-Zoom/Unzoom with two finger (one hand or two handed) - touchpad & screen
-getting the pen working, it worked on other dists. Currently, it write offset like 5 cm. also, pressure sensitivity doesn't work.

Thanks for and hints

---

