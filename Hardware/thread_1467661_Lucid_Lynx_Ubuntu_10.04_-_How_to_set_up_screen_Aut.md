---
title: "Lucid Lynx Ubuntu 10.04 - How to set up screen Auto Rotation on Toshiba Portege M200"
date: 2010-04-30
forum: Hardware
---

### Post by grummy8 on 2010-04-30
[SIZE=2]Hi,
I've just installed Lucid Lynx LTS yesterday on my Tablet Toshiba Portege M200,
Graphics, internet, pressure sense on mypaint works straight out from the box. And the boot time 2x faster than my Windows Xp

Now, I need help to set up screen auto rotation. A step by step instruction would be much appreciate since I'm such a beginner. [/SIZE]

---

### Post by Favux on 2010-05-01
Hi grummy8,

Welcome to Ubuntu Forums!

You need xsetwacom rotation commands which you can set up in a script and run from a launcher or bind to a key.  Unless you use wacom sections in xorg.conf where you've specified Identifiers like stylus, eraser, etc. the old rotation scripts won't work for you.  The new naming convention is longer and more descriptive.  To find what stylus and etc. is being called now enter into a terminal:
```
xinput --list
```

---

### Post by Perkins on 2010-05-01
Ok.  I've got an M700.  I never did get automatic rotation to work, but that's largely because I don't care.  Setting up on-demand rotation is actually not too bad though.


First, xinput --list will give you a list of devices.  Then you write a small bit of script.

```

#! /bin/bash

if [ -f /tmp/rotated ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet eraser" Rotate none
        xsetwacom set "Serial Wacom Tablet" Rotate none
        rm -f /tmp/rotated && exit 0
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet" Rotate CCW
        xsetwacom set "Serial Wacom Tablet eraser" Rotate CCW
        echo 1 > /tmp/rotated && exit 0
fi

```

Change the device names to match whatever the device names were in your xinput output.

I named this script .rotate.sh (so it's hidden and doesn't get accidentally deleted) and stuck it in my home directory.

Next, while we're dealing with xinput, I don't know about your model, but on mine the stylus buttons are all screwy.  The click button is a middle click, and the eraser is a left click.  There's no way to do a right click.  So:

xinput set-button-map "Serial Wacom Tablet eraser" 2
xinput set-button-map "Serial Wacom Tablet" 1 3 2

This makes the click button a right click and the eraser a middle click.  Put those two lines into your Startup Applications.  Again, make the device names match whatever you got from xinput --list.

Now, I can't manage to do automatic rotation, but xbindkeys will let you assign commands to the buttons on the screen bezel.  So you'll need to install xbindkeys.  Then you can use xbindkeys-config to make pressing the rotate button (or whichever button you want) run the rotate script.  It's simple enough I'm going to assume you can figure out how it works.

To make the key assignment permanent, you need to add xbindkeys to your Startup Applications.  (Just the daemon though, not xbindkeys-config.) ;)


That should pretty well do it.  Make any alterations necessary to the parameters and go for it.

---

### Post by Favux on 2010-05-01
Nice work Perkins!

You can also look at the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") for more scripts and wacomrotate along with more info. on key binding and/or setting up launchers.

---

### Post by grummy08 on 2010-05-03
Hi Favux, 
Thanks for such a quick reply, here it goes:


&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]



> **Favux said:**
> Hi grummy8,

Welcome to Ubuntu Forums!

You need xsetwacom rotation commands which you can set up in a script and run from a launcher or bind to a key.  Unless you use wacom sections in xorg.conf where you've specified Identifiers like stylus, eraser, etc. the old rotation scripts won't work for you.  The new naming convention is longer and more descriptive.  To find what stylus and etc. is being called now enter into a terminal:
```
xinput --list
```

---

### Post by Favux on 2010-05-03
Hi grummy08,

Alright, so now we know:

stylus = "Serial Wacom Tablet" or 13

eraser = "Serial Wacom Tablet eraser" or 12

Now just like Perkins did you substitute the new longer device name in (with the quotes) or the number in the rotation script of your choice.  Notice I linked you to the rotation HOW TO which has scripts and instructions on how to set up a launcher or bind the script to a key.

---

### Post by grummy08 on 2010-05-03
Hi Perkins,
Since I used to read e-book and mypaint alot, I need the screen rotation so badly.

I will try your code and see what happen , Thank you





> **Perkins said:**
> Ok.  I've got an M700.  I never did get automatic rotation to work, but that's largely because I don't care.  Setting up on-demand rotation is actually not too bad though.


First, xinput --list will give you a list of devices.  Then you write a small bit of script.

```

#! /bin/bash

if [ -f /tmp/rotated ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet eraser" Rotate none
        xsetwacom set "Serial Wacom Tablet" Rotate none
        rm -f /tmp/rotated && exit 0
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet" Rotate CCW
        xsetwacom set "Serial Wacom Tablet eraser" Rotate CCW
        echo 1 > /tmp/rotated && exit 0
fi

```Change the device names to match whatever the device names were in your xinput output.

I named this script .rotate.sh (so it's hidden and doesn't get accidentally deleted) and stuck it in my home directory.

Next, while we're dealing with xinput, I don't know about your model, but on mine the stylus buttons are all screwy.  The click button is a middle click, and the eraser is a left click.  There's no way to do a right click.  So:

xinput set-button-map "Serial Wacom Tablet eraser" 2
xinput set-button-map "Serial Wacom Tablet" 1 3 2

This makes the click button a right click and the eraser a middle click.  Put those two lines into your Startup Applications.  Again, make the device names match whatever you got from xinput --list.

Now, I can't manage to do automatic rotation, but xbindkeys will let you assign commands to the buttons on the screen bezel.  So you'll need to install xbindkeys.  Then you can use xbindkeys-config to make pressing the rotate button (or whichever button you want) run the rotate script.  It's simple enough I'm going to assume you can figure out how it works.

To make the key assignment permanent, you need to add xbindkeys to your Startup Applications.  (Just the daemon though, not xbindkeys-config.) ;)


That should pretty well do it.  Make any alterations necessary to the parameters and go for it.

---

### Post by grummy08 on 2010-05-03
I got stuck in xbindkeys-config because there is 3 buttons on the bezel of Portege M200 - one of them is dedicated from windows to rotate the screen.

One other thing, it seems that I can't edit all those scripts from copy paste. So I have to type everything from scratch. Well, it felt like a real programmer.

---

### Post by phibuntu on 2010-06-08
Hi

Updating to Lynx braugth a change in the command xsetwacom.

I changed my rotate.sh script to the following, which I added with xbindkeys-config to the "rotate-button" on my lenovh X61. On the toshiba I don't know the button to preferably assign the rotate-functionality; but could be usefull vor others.
The main point I had to change are the arguments of xsetwacom which do not allow 0, 1, 2, 3 any more, but have to be "NONE", "CW", "CCW", "HALF".

Hope it helps.

```
#!/bin/bash

# Infos
# mit xinput list "device name" finden
# mit xbindkeys-config diese Datei an den "rotate-button" hängen
# mit xrandr den Bildschirm drehen (+ output device finden)
# mit "xsetwacom set ..." den "Stylus" "mitdrehen"

# um xsetwacom Device (hier "Wacom Serial..." oder "stylus") zu finden, ist
#    >xinput --list zu starten und dort nachzulesen (bug in Jaunty = Ubuntun 9.04??)
#stylus_name="stylus"
#stylus_name="Wacom Serial Tablet PC Pen Tablet/Digitizer"
stylus_name="Serial Wacom Tablet"

# phi 2009: Karmik achtung: device nicht mehr LDDS
# gefunden mit Kommando "xrandr"
#output=LDDS
output=LVDS1

if [ "$XROT_OUTPUT" ] ; then
         output=$XROT_OUTPUT;
fi

# Die alte Drehrichtung kann mit "xrandr" ermittelt werden.
# Wenn vor der Klammer '(' "left", "inverted" oder "right" steht, dann
# ist das Stylus gedreht.

case `xrandr --verbose | grep "^$output " | sed "s/^[^ ]* [^ ]* [^ ]* ([^(]*) \([a-z]*\).*/\1/"` in
  left)           geom=1;;
  inverted)       geom=2;;
  right)          geom=3;;
  *)              geom=0;;
esac

echo "alte Drehrichtung: $geom"
#neue drehrichtung durch +3 %4 errechnen:
let geom=${geom}+3
let geom=${geom}%4
echo "neu berechnete Geometrie: $geom"

case $geom in
         1)      wacom_orientation=CCW ; xrandr_orientation=left     ;;
         2)      wacom_orientation=HALF; xrandr_orientation=inverted ;;
         3)      wacom_orientation=CW  ; xrandr_orientation=right    ;;
         *)      wacom_orientation=NONE; xrandr_orientation=normal   ;;
esac

#echo "xrandr to $xrandr_orientation, xsetwacom to $wacom_orientation" >&2


## Schritt 1 : Schirm drehen
xrandr --output "$output" --rotate "$xrandr_orientation"

## Schritt 2 : Stift drehen
xsetwacom set "$stylus_name" Rotate $wacom_orientation
```

---

### Post by henry_k on 2010-10-03
Hello all.

I'd love to be able to:

1. Do autorotation
2. Do rotation
3. Do gestures

under Ubuntu 10.04.1 in HP tx2.

Beginning with autoration, I followed the suggestion by Perkins (post 3) 
and changed the old script (for Ubuntu 9), i.e. 

#!/bin/sh
OLDMODE=$(cat /sys/devices/platform/hp-wmi/tablet)
while true; do
    MODE=$(cat /sys/devices/platform/hp-wmi/tablet)
    if [ "$MODE" != "$OLDMODE" ]
    then
        #echo "$MODE - $OLDMODE"
        case "$MODE" in
            "0")
                # Do something
                echo "Normal mode"
                xrandr -o normal 
                xsetwacom set stylus rotate NONE 
                xsetwacom set touch rotate NONE 
                #xsetwacom set eraser rotate NONE
                #cellwriter --hide-window
                ;;
            "1")
                # Do something else
                echo "Tablet mode"
                xrandr -o inverted 
                xsetwacom set stylus rotate HALF 
                xsetwacom set touch rotate HALF 
                #xsetwacom set eraser rotate HALF 
                #cellwriter --show-window
                ;;
        esac
        OLDMODE=$MODE
    fi
    sleep 2s


to


#!/bin/sh
OLDMODE=$(cat /sys/devices/platform/hp-wmi/tablet)
while true; do
    MODE=$(cat /sys/devices/platform/hp-wmi/tablet)
    if [ "$MODE" != "$OLDMODE" ]
    then
        #echo "$MODE - $OLDMODE"
        case "$MODE" in
            "0")
                # Do something
                echo "Normal mode"
                xrandr -o normal 
                "N-Trig Touchscreen" set "N-Trig Pen" rotate NONE 
                "N-Trig Touchscreen" set "N-Trig MultiTouch" rotate NONE 
                #xsetwacom set eraser rotate NONE
                #cellwriter --hide-window
                ;;
            "1")
                # Do something else
                echo "Tablet mode"
                xrandr -o inverted 
                "N-Trig Touchscreen" set "N-Trig Pen" rotate HALF 
                "N-Trig Touchscreen" set "N-Trig MultiTouch" rotate HALF 
                #xsetwacom set eraser rotate HALF 
                #cellwriter --show-window
                ;;
        esac
        OLDMODE=$MODE
    fi
    sleep 2s

Well, there must be more to it than that, but what are the other steps I should be taking? I imagine I have to add lines to /etc/modules and to /etc/X11/xorg.conf , but precisely what? Anything else still?

To be sure, I have great difficulty reading the language of experts.

Hope I am not bothering people too much.

Henry

---

### Post by Favux on 2010-10-03
Hi Henry,

For auto-rotation try Magick 0.5 "4) Rotation to tablet" at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  For rotation see the scripts there also.  In Lucid your touch is most likely on the evdev driver.

For gestures you'd have to clone the xf86-input-wacom git repository.  Also described on the HOW TO.

---

### Post by henry_k on 2010-10-04
Thank you, Favux.

I looked at the N-trig HOW TO and found it all very overwhelming. I know you have been working very hard on this issue and as a Ubuntu user your efforts are much appreciated. But I am a simple soul and find it all difficult to follow; moreover, I am afraid that by making mistakes I am damaging my system to a point that it interferes with my regular, fairly intensive, everyday working use of my tx2.

I had hoped for a simple straight-foward step-by-step adapted to my tx2z-1244ca.
 
Maybe I better wait for further updates/upgrades in Ubuntu(?)

Best,

Henry

> **Favux said:**
> Hi Henry,

For auto-rotation try Magick 0.5 "4) Rotation to tablet" at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  For rotation see the scripts there also.  In Lucid your touch is most likely on the evdev driver.

For gestures you'd have to clone the xf86-input-wacom git repository.  Also described on the HOW TO.

---

### Post by Favux on 2010-10-04
Hi Henry,

I know it's complicated.  But it is doable.  The main thing on Lucid is to upgrade your firmware and then your hid-ntrig.ko.  After that it's a simple change to the 10-wacom.conf file, if even needed, to get the stylus on the wacom driver and touch on the evdev driver.

Going on to get multitouch/gestures on the wacom driver requires a few more steps.

Maverick is looking good for the N-trigs.  It looks like it will work out of the box.  Apparently this is because Ubuntu decided to use the TX2z as a test bed for its new multitouch stack.  I'm guessing that the hid-ntrig.ko for the Maverick kernel is Rafi's 5-4-10 version, or close enough.  Although no one, including Rafi, has confirmed that.  So you can wait just about 8 days for Maverick (out 10-10-10).

But you may/probably will still want to update your firmware.  And to get multitouch its looking like you'll have to wait to the release after Maverick.  I'm not sure its active in Maverick yet.  Unless you want to try putting touch on the wacom driver anyway.

---

### Post by Perkins on 2010-10-04
When the how-tos have you change configuration files, make backup copies of them first.  Preferably include the date as part of the backup file name.  Then, if you screw anything up, you can put it all back just by going to / running find | grep *datestamp* to find all the files you changed, and putting them all back.

Also, if you have a large disk somewhere that you can use, clonezilla will make a nice, whole-system backup, just in case the whole thing falls apart.

---

### Post by henry_k on 2010-10-04
Hi Favux.

Again, thank you for your response, which certainly clarified a lot. I take it that with upgrading the firmware you mean upgrading the N-trig driver from what we have in Windows 7 to the latest version. I am puzzled by the need for using Wacom-related insertions. I would have thought that N-Trig would have taken care of the entire thing. From this remark you may perceive my problem: being puzzled on what fits together with what and why it does so.

Upon checking I learned that the release of Meerkat will be only six days away and so I believe that the wisest thing to do is to wait a week, then see where we stand and just what needs further touch-ups. I imagine that Meerkat will not be upgrading firmware for us and that this is something we shall need to do ourselves. As John Way used to say, "We shall see what we shall see."

Best,

Henry

BTW. The last post by Perkins certainly boot a bee in my bonnet! Thanks for that. Would it not be nice to have a consumer type monthly magazine to keep plain, ordinary Ubuntu users up to scratch on what developments have occurred or are occurring and how to profit from them and do so in a style engaging OS users. But then again, even so, some experience working the command-line will probably still be essential. H.

> **Favux said:**
> Hi Henry,

I know it's complicated.  But it is doable.  The main thing on Lucid is to upgrade your firmware and then your hid-ntrig.ko.  After that it's a simple change to the 10-wacom.conf file, if even needed, to get the stylus on the wacom driver and touch on the evdev driver.

Going on to get multitouch/gestures on the wacom driver requires a few more steps.

Maverick is looking good for the N-trigs.  It looks like it will work out of the box.  Apparently this is because Ubuntu decided to use the TX2z as a test bed for its new multitouch stack.  I'm guessing that the hid-ntrig.ko for the Maverick kernel is Rafi's 5-4-10 version, or close enough.  Although no one, including Rafi, has confirmed that.  So you can wait just about 8 days for Maverick (out 10-10-10).

But you may/probably will still want to update your firmware.  And to get multitouch its looking like you'll have to wait to the release after Maverick.  I'm not sure its active in Maverick yet.  Unless you want to try putting touch on the wacom driver anyway.

---

### Post by Ayuthia on 2010-10-04
> **henry_k said:**
> Hi Favux.

Again, thank you for your response, which certainly clarified a lot. I take it that with upgrading the firmware you mean upgrading the N-trig driver from what we have in Windows 7 to the latest version. I am puzzled by the need for using Wacom-related insertions. I would have thought that N-Trig would have taken care of the entire thing. From this remark you may perceive my problem: being puzzled on what fits together with what and why it does so.

Upon checking I learned that the release of Meerkat will be only six days away and so I believe that the wisest thing to do is to wait a week, then see where we stand and just what needs further touch-ups. I imagine that Meerkat will not be upgrading firmware for us and that this is something we shall need to do ourselves. As John Way used to say, "We shall see what we shall see."

It is nice to hear from you again.

It would not be too bad to wait for Meerkat to come out.  However, the current Windows 7 firmware has been the best one to use so far for me.  Unfortunately, N-trig has not released a firmware installer for Linux yet (so no firmware update in Meerkat).  They have also not released an xorg driver that will work with their device as of yet either (and that is why we are still using Wacom and evdev).  It has been a few months since I have seen any updates from N-trig through the input mailing list.

So at this time, we are still using Wacom for the stylus.  For the touch though, it has been recommended to use the evdev driver instead of the Wacom driver like we did in versions prior to Lucid.  Lucid and Meerkat should be defaulting to that upon a fresh install.  The multitouch development has started in Meerkat and hopefully we shall see more in the 11.04 release.

---

### Post by Ayuthia on 2010-10-04
> **Favux said:**
> I'm guessing that the hid-ntrig.ko for the Maverick kernel is Rafi's 5-4-10 version, or close enough.  Although no one, including Rafi, has confirmed that.  So you can wait just about 8 days for Maverick (out 10-10-10).


The kernel that is being used in Maverick should be the most current version out there.  I don't recall any updates that have been made in 2.6.36.  Rafi has been the supplying the last few updates so I am fairly confident in saying that Maverick is up to date.

---

### Post by henry_k on 2010-10-05
Thanks, Ayuthia. From your and Favux's comments I am getting some idea of what to do, but I'll just lay low for the rest of the week to try out Meerkat first. Then I make some from the ground up "plan of action" and submit it on this forum for expert critique before getting myself into a mess.

Henry

---

