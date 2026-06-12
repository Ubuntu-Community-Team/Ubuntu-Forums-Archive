---
title: "LG C1 Touchscreen Installation"
date: 2010-11-22
forum: Hardware
---

### Post by zeronius on 2010-11-22
Heelo out there,

im a littlebit confused. i tried to install ubuntu 10.10 on my old LG C1. all works fine or i figured out for myself, but i dont how to handle this problem.

i know it is possible because i found this sites and guides:

[http://www.gentoo-wiki.info/LG_C1#Tablet](http://www.gentoo-wiki.info/LG_C1#Tablet)

[http://ubuntuforums.org/showthread.php?t=441723&page=4](http://ubuntuforums.org/showthread.php?t=441723&page=4)

problem: i dont really know what i have to do and even dont know ubuntu detect the touch screen.

i found some drivers here:

[http://www.conan.de/touchscreen/p-series.html#download](http://www.conan.de/touchscreen/p-series.html#download)

[http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html](http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html)

and in the package list the

xserver-xorg-input-fpit

package, but it doesnt work. when i try to install it, the little basterd wants to change a everything and ubuntu says no.

please anybody help me!

sorry for my english!

---

### Post by Favux on 2010-11-22
Hi zeronius,

Welcome to Ubuntu forums!

It looks like the last fpit driver package was built for Lucid (10.4 LTR):  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=fpit&field.status_filter=published&field.series_filter=lucid](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=fpit&field.status_filter=published&field.series_filter=lucid)

It doesn't look like it has been built for Maverick (10.10)

---

### Post by zeronius on 2010-11-22
hi Favux. Thanks for fast reply.

i tried it first in 10.04. it doesnt work there,too. hoped an update solves some of my problems, and under 10.10 my touchpad works better, but still have problems with the touchpad keys.
maybe the input devices touchpad and touchscreen work togehther in one strange way?

i tried ectouch, fpit packages and the sources from other sites, even ppa (called so?)

maybe i found my correct drivers i dont know ubuntu detect my usb devices corectly. how can i figure it out? all work is sensless when i have to detect the device first...

oh my god, im so n00b^^

---

### Post by Favux on 2010-11-22
Since it there is a Lucid fpit package I'd say Lucid is your best shot.  Maybe you hadn't configured things correctly yet?

Well the digitizer would be serial.  First try:
```
more /proc/bus/input/devices
(and/or)
grep -i name /proc/bus/input/devices
```
and see if the digitizer is recognized.

Or you could try to listen in on the serial ports.
```
xxd /dev/ttyS0
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use in xorg.conf.

---

### Post by zeronius on 2010-11-22
thank you for your time :)

ok, so far i tried:

more /proc/bus/input/devices


and ot several devices, but shortly:
```
grep -i name /proc/bus/input/devices
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Power Button"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="SynPS/2 Synaptics TouchPad"
N: Name="Bluetooth Travel Mouse"

```i think its not in the list.

for your second part:


xxd /dev/ttyS*

i got:
```
ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3

```with xxd only in ttyS0 something happend, but nothing to see. have to leave with strg^c. in the rest i got only a new line:

```
root@heracles:~# xxd /dev/ttyS0
^C      
root@heracles:~# xxd /dev/ttyS1
root@heracles:~# xxd /dev/ttyS2
root@heracles:~# xxd /dev/ttyS0
^C      

```so far, any ideas? 
:cool:

---

### Post by Favux on 2010-11-22
Did you try to install the Lucid fpit driver in Maverick?  Does it install?  Have you googled to see if anyone has updated fpit for Maverick?

If not I think we should try Lucid.  Install the fpit driver package and then try the above commands again.

Does that make sense to you?

---

### Post by zeronius on 2010-11-22
make sense to me so far.

but i tried lucid and there is the same problem with the package via synaptic. in the graphic intrface it wants to remove all in the xserver from ubuntu-desktop, xorg, xorg-core and the most of xorg-input and -video.

in terminal:
```
Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 xserver-xorg-input-fpit : Hängt ab von: xserver-xorg-core (>= 2:1.5.99.901) soll aber nicht installiert werden
E: Beschädigte Pakete
```

sorry for language, but i think the error message looks similiar in english. 
after that, i tried 10.10 and wanted to look how parts now change. 
i found a 2-years old discussion about fpit and, now i remember your avatar Favux :cool: :

[http://wiki.ubuntuforums.org/showthread.php?t=1370842](http://wiki.ubuntuforums.org/showthread.php?t=1370842)

---

### Post by Favux on 2010-11-22
Hi zeronius,

So the following package fpit is hanging on Xserver >= 1.5.99.  That's weird because as your link showed it built in Karmic which was 1.6.  You are right not to let it uninstall your Xserver!!!

So Lucid is 1.7 and Maverick 1.9.  I was looking at this bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540)  and that led me to:  [http://www.ubuntuupdates.org/packages/show/228060](http://www.ubuntuupdates.org/packages/show/228060)

So it looks like a fpit package was built for Maverick in Universe.  There doesn't seem to be a package there to download though.

---

### Post by zeronius on 2010-11-24
oh, thank you. first problem solved: i think i found the correct howto with wrong drivers. 
now i was able to install the xserver-xorg-input-fujitouch without removing X ^^

it dont work now, i think i have to wright something into something. conan says in xorg.conf , but i read that xorg.conf in ubuntu 10.+ is working in another way than the usual.

where i have to insert the lines:

```
Section "InputDevice"
    Identifier "touchscreen"
    Driver  "fujitsu"
    Option  "Device" "/dev/ttyS0"
    Option  "DeviceName" "touchscreen"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036"
    Option  "MaxY"        "3999"
    Option  "SendCoreEvents" "On"
EndSection
```and

```
InputDevice "touchscreen" "CorePointer"
```

in the tty files?

i still dont know ubuntu recognized the touchscreen....

nice day everyone :cool:

zeronius

---

### Post by Favux on 2010-11-24
Hi zeronius,

It would be a good thing if you could explain how you installed the fpit driver, what version you used, and link to where you got it.

There are two ways to configure in Lucid and Maverick.  The xorg.conf or using a .conf file in xorg.conf.d (/usr/lib/X11/xorg.conf.d/ in Lucid; /usr/share/X11/xorg.conf.d/ in Maverick).  Since you are in Maverick look for a xx-fpit.conf file at /usr/share/X11/xorg.conf.d/.  The fpit driver package may have installed one.  If you have one post it.  You should only use the .conf file or the xorg.conf.  Not both.

The only reason to use a .conf file is to hot plug a usb device.  Since you have a tablet pc you don't need to hot plug it.  Especially since it is serial and won't hot plug anyway.  So for you using the xorg.conf to configure is fine.

If you have a xorg.conf file in /etc/X11 could you post it before you make any changes?  Starting with Lucid/X server 1.7 core events is assumed, so the fpit section should look something like:
```
Section "InputDevice"
    Identifier "fujitsu touchscreen"
    Driver  "fujitsu"
    Option  "Device" "/dev/ttyS0"
#    Option  "DeviceName" "touchscreen"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036"
    Option  "MaxY"        "3999"
EndSection
```
Depending on whether you have an xorg.conf with video sections, the "ServerLayout" might look something like:
```
Section "ServerLayout"
    Identifier	"X.org Configured"
    InputDevice "fujitsu touchscreen"
EndSection
```
Always remember to back up a working xorg.conf file and be prepared to restore it from the command line in case you break X.

---

### Post by zeronius on 2010-11-24
hi Favux,

argh, cant remember exactly where exactly i downloaded it. think i added ppa sources to my package list and found -fujitsu and not -fpit. in describtion:

This package is based on the work done in: [http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html)

so my xorg.conf.d looks like:

```
10-evdev.conf      50-vmmouse.conf  51-synaptics-quirks.conf
50-synaptics.conf  50-wacom.conf    60-magictrackpad.conf

```

added are evdev, synaptics-quirks, wacom, and magictrackpad. im a littlebit confused about that. i dont have a xorg.conf file, only the xorg.conf.d.

the 50-wacom:

```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
 Option "Button2" "3"
EndSection
```

"Magic Trackpad"

```
Section "InputClass"
         Identifier "Magic Trackpad"
         MatchUSBID "05ac:030e"
         Driver "evdev"
EndSection

```

had not enough time the last 2 days, but when im think about, it looks not as the correct driver.

---

### Post by Favux on 2010-11-24
OK, don't worry about the .conf files in xorg.conf.d then.  None of them apply to your tablet pc.

I don't think the fujitouch driver will work for your tablet.  If I remember correctly it does need the fpit driver.  It has a Fine Point digitizer (that's where the fpit comes from).  So your stylus/pen has a battery, correct?  Anyway I think finepoint went out of business a couple years ago, shortly after your tablet came out.

But it's a serial driver so worth a chance.  Create your own xorg.conf with:
```
gksudo gedit /etc/X11/xorg.conf
```
and enter into it (copy & paste) just what I gave you:
```
Section "InputDevice"
    Identifier "FinePoint touchscreen"
    Driver  "fpit"
    Option  "Device" "/dev/ttyS0"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036"
    Option  "MaxY"        "3999"
EndSection

Section "ServerLayout"
    Identifier	"X.org Configured"
    InputDevice "FinePoint touchscreen"
EndSection
```
Be sure to be ready to remove this xorg.conf from the command line if it breaks X.  And the coordinates are probably wrong for your tablet so be ready to comment (#) them out.


Edit:  Change from fujitsu driver to fpit.  And changed identifier to FinePoint.  I think that's who made the digitizer/touchscreen.

---

### Post by Favux on 2010-11-24
Alright, I just cloned the Debian git repostiory of fpit in Lucid (compiled fpit in other words) and it seemed to install fine.  Of course I don't have a tablet to test.  I have the instructions for you.  The only problem is there may be libraries you need to install that I don't notice because I already have them installed.  So you would have to copy your terminal output and be prepared to post it if needed.  So I can figure out what libraries are needed.

Let's see if I can do it in Maverick or if I run into the unmet dependencies they are talking about.

---

### Post by Favux on 2010-11-25
OK, it worked in Maverick to.  By the way I checked in Synaptic Package Manager and fpit was there and when I tried to install it in Lucid and Maverick I got the same as you did.  It wanted to remove:
```
fglrx
fglrx-amdcccle
ubuntu-desktop
xorg
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-*
xserver-xorg-video-all
xserver-xorg-video-*
```
That's crazy, that would disable your system.  This should be filed as a high priority bug on Launchpad.  Something is very wrong with it's packaging.

Anyway just because it compiles doesn't mean it's going to work.  But try cloning the fpit git repository by copying and pasting each of the following commands in a terminal:
```
cd ./Desktop

git clone git://anongit.freedesktop.org/xorg/driver/xf86-input-fpit

sudo apt-get update

sudo apt-get install build-essential libxrandr-dev x11proto-input-dev xserver-xorg-dev xutils-dev autoconf libtool pkg-config

sudo apt-get upgrade

cd xf86-input-fpit

./autogen.sh --prefix=/usr

make

sudo make install

(Now reboot.)
```
That's my best guess at the libraries you'll need.  I could have too many or may have missed a few.  So save the outputs of the configure and make lines and I should be able to figure out what's missing from them.

Then we need to modify your xorg.conf a little.  Change:
```
    Driver  "fujitsu"
```
or
```
    Driver  "fpit"
```


Edit:  Added  xutils-dev to dependency line.

---

### Post by zeronius on 2010-11-25
uhooo favux,
sounds like you have spend a lot of time in my problem. Thousands thanks :D i will work through the next hours.
the touchscreen of the LG C1 is an resistive panel. i dont need a special pen, only the tip has to be soft enough to make no scratches. one-point finger input is allowed, too.
if i remember correctly the fuji-P-series had the same input, except of my old asus R1F, there was the case you are talking about. the panel detected the pencil even a few mm above the panel, but no finger input. 
that input was really annoying, because the localisation was a crap, especially on the edges!

i will make it and let you know hopefully about victory^^


EDIT:

so far, i made all you told me.

1.) edit with
```
gksudo gedit /etc/X11/xorg.conf
```xorg to:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "InputDevice"
    Identifier "fujitsu touchscreen"
    Driver  "fujitsu"
    Option  "Device" "/dev/ttyS0"
#    Option  "DeviceName" "touchscreen"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036"
    Option  "MaxY"        "3999"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice "fujitsu touchscreen"
EndSection
```
2.)install package with xorg-macros
feed terminal line per line with your coammd-lines

procedure as attachment

now i reboot and and see what happen :)

---

### Post by zeronius on 2010-11-25
so far, still dont work, but X is not crashing. now i rename in xorg.conf  Driver "fujitsu" in "fpit" and let us see what happens....

IT WORKS!

after rename Driver in "fpit" and reboot it works! the touchscreen behaves strange (tip on screen and cursor jumps in a corner) but i think i have to play with the preferences. 
littlebit strange, because in the xorg.conf are the same preferences for the axis like in the gentoo wiki:

```

 Section "ServerLayout"
   ....
        InputDevice    "touchscreen" "SendCoreEvents"
 EndSection

 Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
 EndSection

```

but it is alive! XD

---

### Post by Favux on 2010-11-25
Hi zeronius,

Good!  Sounds like something happened.  Let's look at:
```
xinput --list
```
Did the system tell you to install xorg-macros?  Or did you figure it out?  Either way it needs to be in the dependency line.

Where did the nvidia video sections come from?  Did you install the proprietary drivers?

Let me look at your output.

---

### Post by zeronius on 2010-11-25
hi master favux :cool:

with 
xinput --listi got 
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TOUCHSCREEN                                 id=6    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Travel Mouse                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

while the installation it told me, that it cant proceed without xorg-macros. after google i figured out that i have to install xutils-dev to manage the problem. so i did.
yes, i use the proprietary drivers of nvidia.
the bluetooth mouse i have to use because of the strange behavier of the touchpad^^ (my way to handle some problems).

---

### Post by Favux on 2010-11-25
So we just need to add xutils-dev to the dependency line.  Good.

The good news is the system is now seeing the touchscreen:
```
&#9116;   &#8627; TOUCHSCREEN                                 id=6    [slave  pointer  (2)]

```
By the way that's why I wanted to change it to "Fujitsu Touchscreen" so it was obvious.  But actually "FinePoint Touchscreen" would be better wouldn't it?

Did you get the coordinates from another LG C1 post?

---

### Post by zeronius on 2010-11-25
yeah, i have the coordinates from the lg c1 gentoo wiki, see my post above:
> the gentoo wiki:

 	Code:
 	 Section "ServerLayout"
   ....
        InputDevice    "touchscreen" "SendCoreEvents"
 EndSection

 Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
 EndSection 


thats exactly your min/max coordinates. i search the web for another port, think i found two another, and will see what others have done.

---

### Post by Favux on 2010-11-25
At this point, since we have some fpit driver function, it would be good to look at your Xorg.0.log.  It's in /var/log.  That may tell us some of what's going on.

---

### Post by zeronius on 2010-11-25
ok, i attachted it. 
shortly i found this section:

```
40.254] (**) TOUCHSCREEN: always reports core events
[    40.254] (**) FPIT device name: TOUCHSCREEN
[    40.254] (**) Fpit associated screen: 0
[    40.254] (**) FPIT maximum x position: 4100
[    40.254] (**) FPIT minimum x position: 0
[    40.254] (**) FPIT maximum y position: 4100
[    40.254] (**) FPIT minimum y position: 0
[    40.254] (**) FPIT invert X axis: No
[    40.254] (**) FPIT invert Y axis: No
[    40.254] (**) FPIT swap X and Y axis: No
[    40.254] (**) FPIT Passive button mode: No
[    40.254] (**) FPIT RandR tracking: No
[    40.254] (II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
[    40.254] (**) Option "Device" "/dev/ttyS0"
[    40.254] (**) Option "BaudRate" "19200"
[    40.254] (**) Option "StopBits" "0"
[    40.254] (**) Option "DataBits" "8"
[    40.254] (**) Option "Parity" "None"
[    40.254] (**) Option "Vmin" "10"
[    40.254] (**) Option "Vtime" "1"
[    40.254] (**) Option "FlowControl" "None"
[    40.269] (II) config/udev: Adding input device Power Button (/dev/input/event3)
```

and what means this part from the touchpad:
```
[    40.350] (**) Option "Device" "/dev/input/event6"
[    40.401] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    40.401] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    40.401] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    40.401] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    40.401] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    40.440] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    40.445] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    40.465] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    40.465] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    40.465] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    40.465] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    40.465] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    40.489] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    40.489] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    40.489] (II) No input driver/identifier specified (ignoring)
[   259.212] (II) config/udev: Adding input device Bluetooth Travel Mouse (/dev/input/mouse1)
[   259.212] (II) No input driver/identifier specified (ignoring)
```
is that my touchpad section?

---

### Post by Favux on 2010-11-25
OK, it looks like the fpit driver is taking your tablet!  Here is an old 'man fpit' page:  [http://linux.die.net/man/4/fpit](http://linux.die.net/man/4/fpit)  Check in a terminal if there is a newer one 'man fpit'.  If so please post it.

As you can see it's important to know if your stylus has a battery (active) or if it doesn't (passive).  Does it have a battery?


Looks like your Synaptic touchpad.  Something may be a little flaky.  Hard to tell.  Is the touchpad working?  If so let's not worry about it.

---

### Post by zeronius on 2010-11-25
na, toucpad works, but how i wrote in my first post, the buttons make double click and a scroll, but i will take care about it in another post.

its defently a resistive touchscreen with wired input, i dont need a battery for the pencil.i can use what ever i want (and dont make scratches).


i tried to figure out what can i do. first difference was the variable **Option *"MaximumXPosition" "number" ***instead of "MaxX", dont know it makes realy a difference.

cursor still jumps around. i used settings from:

[http://wiki.ubuntuforums.org/showthread.php?t=1370842](http://wiki.ubuntuforums.org/showthread.php?t=1370842)

and 

[http://www.gentoo-wiki.info/LG_C1#Tablet](http://www.gentoo-wiki.info/LG_C1#Tablet)

but it still jumps around.

i would now try to manipulate the xorg.conf file like the guy in the first link.

---

### Post by Favux on 2010-11-25
OK, no battery.  Have you tried this Option?:
```
    Option  "Passive"
```
so you have:
```
Section "InputDevice"
    Identifier "FinePoint touchscreen"
    Driver  "fpit"
    Option  "Device" "/dev/ttyS0"
    Option  "Passive"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036"
    Option  "MaxY"        "3999"
EndSection
```
Also since you have the proprietary Nvidia driver you might want to try:
```
Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
#    Identifier	"X.org Configured"
    InputDevice "FinePoint touchscreen"
EndSection
```
I don't know if it will make any difference.

---

### Post by zeronius on 2010-11-25
so, i made the new xorg.conf 

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputDevice"
    Identifier "FinePoint touchscreen"
    Driver  "fpit"
    Option  "Device" "/dev/ttyS0"
    Option  "Passive"
#   Option  "MaximumXPosition"          "4036"
#   Option  "MaximumYPosition"          "4059"
#   Option  "MinimumXPosition"          "82"
#   Option  "MinimumYPosition"          "300"
#   Option  "DeviceName" "touchscreen"
    Option  "MinX"        "82"
    Option  "MinY"        "146"
    Option  "MaxX"        "4036" Option  "MaxY"        "3999"
 EndSection

#Section "ServerLayout"
#    Identifier "X.org Configured"
#    InputDevice "fujitsu touchscreen"
#EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
 Screen      "Default Screen"
#   Identifier  "X.org Configured"
    InputDevice "FinePoint touchscreen"
EndSection
```

but cursor ist still flipping into a corner and i think it make double or triple clicks. maybe the [http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html) -guide is helpful?

good night

zeronius

---

### Post by zeronius on 2010-11-28
ok, i tried a lot.also the tips from conans page, because i thought my cursor is doing the same strange stuff he describes on his hp.
so i tried to insert a dummy mouse, but nothing happened, same behavior. when i tip on my screen, cursor jumps directly to the down/right corner and makes triple click.

think to play with the x-y-axis in the xorg.conf will not help, because of the triple click, but i dont understand what happens, because the driver works and i use the same coordinates from people with the same laptopmodel.

in what depens this stuff?

happy evening 

zeronius

---

### Post by kingpinzs on 2010-12-10
I tryed compiling the ftip driver but I am getting error Need a server with input ABI 12.
 
How do i fix that?

---

### Post by pmsoft1 on 2010-12-30
Hi there,

I'm running Lucid on my LG C1.
First of all, my touchpad has the same behavior: if I click, it's actually a triple click and a scroll. I think there are different versions of this touchpad in the C1/A1 series since some don't experience this. However this is the bug report: [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159968").
And to get the touchscreen working, you I recommend the xserver-xorg-input-fpit (it's in the repositories). You could also compile the [fujitouch]("http://www.conan.de/touchscreen/p-series.html") driver, but it does not support rotation. Sadly for Lucid and I think for Maverick there are unmet dependecies (see [this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540") for a fix).
And for reference this is my xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.21  (buildmeister@builder103.nvidia.com)  Thu Nov  4 20:57:26 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "touchscreen"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "UpDownScrolling" "0"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

#	Option		"MinY"		"146"
#	Option		"MaxX"		"4036"
#	Option		"MaxY"		"3999"
#	Option		"TapTimer"	"120 ms"
#	Option		"SwapX"		"1"
#	Option		"SwapY"		"1"
    Identifier     "touchscreen"
    Driver         "fpit"
    Option         "Device" "/dev/ttyS0"
    Option         "BaudRate" "9600"
    Option         "DeviceName" "touchscreen"
    Option         "MaximumXPosition" "3996"
    Option         "MaximumYPosition" "3999"
    Option         "MinimumXPosition" "60"
    Option         "MinimumYPosition" "146"
#	Option		"MinX"		"82"
    Option         "Passive"
    Option         "SendCoreEvents"
    Option         "TrackRandR"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    Option         "RandRRotation"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Hope that helps.

---

### Post by zeronius on 2011-05-05
any updates since ubuntu 11.04?

i arranged myself with this problems ....mhhh...think i will try it again to fix it

---

### Post by zeronius on 2011-08-12
Hi Guys,

I got it! The most problems are solved:

-Audio works (without special key) with:

[http://www.matrix44.net/blog/?p=688](http://www.matrix44.net/blog/?p=688)

-Touchscreen works fine with the settings from pmsoft1. 

-for rotating you have only to set the option:

Option         "RandRRotation" "True"

found on:

[http://www.gtkdb.de/index_7_1079.html](http://www.gtkdb.de/index_7_1079.html)

now i try to bind the rotation to one of the special keys

and

bind the on screen keyboard to the other

im happy :)

---

