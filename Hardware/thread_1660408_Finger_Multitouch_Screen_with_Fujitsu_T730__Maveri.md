---
title: "Finger Multitouch Screen with Fujitsu T730 // Maverick"
date: 2011-01-05
forum: Hardware
---

### Post by zzzeb on 2011-01-05
Hi all ;
(And happy new year from france!)

OK I received for Christmas the Fujitsu Lifebook T730 but couldn't use finger multitouch on the screen :(

I tried to follow several posts on the forum but were unsuccessful ; and I could not finish the last one I tried : [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

Could someone support me ?

Here are output of xinput --list :

```

seb@LaBestiole:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=15   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=16   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=9    [slave  keyboard (3)]
    &#8627; Power Button                              id=10   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=11   [slave  keyboard (3)]
    &#8627; CNF8248                                   id=12   [slave  keyboard (3)]
    &#8627; fsc tablet buttons                        id=13   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]

```Thanks by advance ; seb.

---

### Post by Favux on 2011-01-05
Hi zzzeb,

Welcome to Ubuntu forums!

Where did you get stuck in the HOW TO?  What did you get done?

---

### Post by zzzeb on 2011-01-05
Hi Favux;

I did number I, III a), and at IV I've not been able to correctly configure the '.xsetwacom.sh'

Here it is with changes I ve done: 

```

## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch, and pad.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = ID 17 = "Serial Wacom Tablet stylus"
xsetwacom set "Serial Wacom Tablet stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
#xsetwacom set "Serial Wacom Tablet stylus" ClickForce "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 17 PressCurve "5 10 90 95"  # Bezier curve, default is 0,0,100,100
xsetwacom set 17 TPCButton "on"  # stylus tip + button, or "off" for hover mode
#xsetwacom set 17 Mode "Absolute"  # or "Relative" cursor movement
xsetwacom set 17 Button1 "1"  # left mouse click
xsetwacom set 17 Button2 "3"  # right mouse click
xsetwacom set 17 Button3 "2"  # middle mouse click

## eraser = ID 16 = "Serial Wacom Tablet eraser"
xsetwacom set 16 Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 16 RawSample "2"  # default is 2, 0-100
#xsetwacom set 16 ClickForce "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 16 Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 16 PressCurve "0 10 90 100"  # Bezier curve, default is 0,0,100,100
#xsetwacom set 16 Mode "Absolute"  # or "Relative" cursor movement
xsetwacom set 16 Button1 "1"

## touch = ID 11 = "Wacom BambooFun 2FG 4x5 Finger touch"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Touch "on"  # or "off"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Gesture "on"  # or "off"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger touch" Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 11 RawSample "2"  #  efault is 2, 0-100
#xsetwacom set 11 ClickForce "27"  # default is 27, range is 0-2047
xsetwacom set 11 Threshold "27"  # default is 27, range is 0-2047
xsetwacom set 11 Mode "Relative"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 11 ZoomDistance "50"  # default is 50
xsetwacom set 11 ScrollDistance "20"  # default is 20
xsetwacom set 11 TapTime "250"  # 2FG R click, default is 250 ms

## pad = ID 10 = "Wacom BambooFun 2FG 4x5 Finger pad"
xsetwacom set 10 Button1 "key ctrl t"  # toggle touch script
xsetwacom set 10 Button2 "key backspace"
xsetwacom set 10 Button3 "3"  # right mouse click
xsetwacom set 10 Button4 "key alt left"  # Back a page in FireFox

## Developed with dr4ziw and iRi_E

```
I changed some part with what I found in xinput --list ; but I m not shure at all!

And this is the answer I've in the terminal :
```

seb@LaBestiole:~$ ./.xsetwacom.sh
Unknown parameter name 'Threshold'.
Unknown parameter name 'Threshold'.
Cannot find device 'Wacom BambooFun 2FG 4x5 Finger touch'.
Cannot find device 'Wacom BambooFun 2FG 4x5 Finger touch'.
Cannot find device 'Wacom BambooFun 2FG 4x5 Finger touch'.
Property 'Wacom Sample and Suppress' does not exist on device.
Unknown parameter name 'Threshold'.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
./.xsetwacom.sh: line 49:  4054 Erreur de segmentation  xsetwacom set 10 Button1 "key ctrl t"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15

```


... :/

---

### Post by Favux on 2011-01-05
OK, you're close.

First Part I. gives you the usb kernel driver wacom.ko.  Since yours is a serial Wacom digitizer with an internal serial connection you don't use it.  What you need is to update your xf86-input-wacom to 0.10-10+, i.e. clone the git repository which is part II.  That's the driver that has the X driver wacom_drv.so that you need.

The updated xf86-input-wacom has fixes for Fujitsu tablets and xsetwacom.  Touch should now show up in xinpput list.  That should get you touch gestures.  The ClickForce command changes names to Threshold which should take care of that error.

The Bamboo .xsetwacom.sh does not serve you well.  You should use the one for the Lenovo X201t in the tablet pc tar attached to post #2.  Other than the coordinates it should be close to what you need.  You can get rid of the single finger touch section.  And you are correct to use the "Device names" xinput list returns for your tablet pc.

---

### Post by zzzeb on 2011-01-05
FAVUX : THANKS =))

Multitouch works now !!!

I didn't understand soo much but it works and THAT IS COOL :)

I couldn't find the .xsetwacom.sh  for the Lenovo X201t you are refering to. But what this file is used for ? What will it change if I put this version ?
And do I have to follow section V as well ?

Thanks anyway!
(I think this was one of the fastest debugging I've never seen ... which means you are good :)

(Anyway I ll post the all commands I did so that others will be able to do it very quickly)

---

### Post by Favux on 2011-01-05
Congratulations!  Nice work.

It's called Sample_usb&serial_tablet-pc's_.xsetwacom.sh's.tar.bz2 attached to post #2 of the HOW TO thread.  The one for the Lenovo Thinkpads X200t & X201t.  It will get rid of some errors you are probably getting because you don't have a pad.  Plus you may want touch absolute (the tablet pc way) rather than relative.

Sure, you can use the toggle touch script described in part V.  You'd have to bind it to another button, say a bezel button, because you don't have pad or tablet buttons.  Or you could put it in a launcher.  If you drag the launcher into a panel (does netbook remix have panels?) it would run with a single click.

---

### Post by zzzeb on 2011-01-05
OK I work on that tomorrow cause I think my brain is tired with English for today... ;)

Will update you when working !

Thank you Favux Ubuntu God =)

++

---

### Post by zzzeb on 2011-01-06
Ok ; with the file you where refering to ([http://ubuntuforums.org/showpost.php?p=9496756&postcount=2](http://ubuntuforums.org/showpost.php?p=9496756&postcount=2))

I ve this result & behavior of multitouch doesn t look like to be modified. In the same time, I don't really know what I should observe. (what's the difference between absolute touch & relative on practical use ?)

```

seb@LaBestiole:~$ ./.xsetwacom.sh
Unknown parameter name 'ClickForce'.
Unknown parameter name 'ClickForce'.
Usage: xsetwacom [options] [command [arguments...]]
Options:
 -h, --help                 - usage
 -v, --verbose              - verbose output
 -V, --version              - version info
 -d, --display disp_name    - override default display
 -s, --shell                - generate shell commands for 'get'
 -x, --xconf                - generate X.conf lines for 'get'

Commands:
 --list [dev|param]           - display known devices, parameters 
 --list mod                   - display supported modifier and specific keys for keystrokes
 --set dev_name param [values...] - set device parameter by name
 --get dev_name param [param...] - get current device parameter(s) value by name
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.

```

For section V, I've buttons on below the screen that I can use for this. Otherwise Ubuntu Netbook has a left panel to lauch application ; I looked a little bit to put a shortcut linked with the .sh but couldn't find the wright menu to do so ; but I think this should be possible.
Anyway I modified the script and it works well :) ; the only problem I ve got is with compiz settings config : I tried to link a simple key combination : Ctrl+G with the toggle script but I can't make it work ... Compiz was not installed at all so I tried lauch compiz-decorator but were unsuccessful ...

---

### Post by zzzeb on 2011-02-20
Conclusions on operations to realize on a Fujitsu 730 to get dual touch  working and some other options (screen rotation, etc...) 
(At least that is what I realized twice and it worked :)

First I installed : 

*Virtual keyboards :
cellwriter
kvkbd

*UTOUCH (not sure very usefull but I installed it) :
utouch
utouch-geis-tool

*For special key : 
Add : **ppa:khnz/ppa**
in order to install :
fsc-btns-kernel-source
fscrotd
fscd
fjbtndrv
(more info on [http://doc.ubuntu-fr.org/fujitsu-siemens_lifebook_t1010#touches_multimedia](http://doc.ubuntu-fr.org/fujitsu-siemens_lifebook_t1010#touches_multimedia))

Then (to insert line by line):

```

cd ./Desktop
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2
sudo apt-get update
sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev  libncurses5-dev
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
tar xjvf linuxwacom-0.8.8-10.tar.bz2
cd linuxwacom-0.8.8-10
./configure --enable-wacom --prefix=/usr
make
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a

```

REBOOT 
(After rebooting if not working check if the wacom.ko is auto-loading with lsmod.)

```

sudo modprobe wacom
lsmod | grep wacom
 
```

(you should see 'wacom' with some other stuff)

```

sudo apt-get install git-core
cd ./Desktop
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
sudo apt-get update
sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev  xutils-dev autoconf libtool pkg-config
sudo apt-get upgrade
sudo apt-get build-dep xf86-input-wacom
 wget http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2
sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
tar xjvf util-macros-1.8.0.tar.bz2
cd util-macros-1.8.0
./configure --prefix=/usr
make
sudo make install
cd ..
cd xf86-input-wacom
./autogen.sh --prefix=/usr
make
sudo make install

```

REBOOT

```

kdesudo kate /usr/share/X11/xorg.conf.d/50-wacom.conf

```

Content of the 50-wacom.conf file :

======================================================
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
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

Section "InputClass"
      Identifier "Wacom eraser class"
      MatchProduct "Wacom"
      MatchProduct "eraser"
      Option "Foo" "bar"
EndSection
===================

Create .xsetwacom.sh in /home/USER with this content:
===================
## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = "Serial Wacom Tablet stylus" = ID 15
xsetwacom set "Serial Wacom Tablet stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet stylus" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet stylus" PressCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet stylus" TPCButton "on  # or is  Relative needed for gestures?"  # stylus tip + button, or "off" for  hover mode
xsetwacom set "Serial Wacom Tablet stylus" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet stylus" Button1 "1"  # left mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button2 "3"  # right mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button3 "2"  # middle mouse click
# sample X200t coordinates, default coordinates in /var/log/Xorg.0.log
#xsetwacom set "Serial Wacom Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## eraser = "Serial Wacom Tablet eraser" = ID 13
xsetwacom set "Serial Wacom Tablet eraser" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet eraser" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet eraser" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet eraser" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet eraser" PressCurve "0 10 90 100" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet eraser" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet eraser" Button1 "1"
# coordinates are the same as used for the stylus
#xsetwacom set "Serial Wacom Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## depending on your model use the applicable following touch section ##

## single finger touch
## touch = "Serial Wacom Tablet touch" = ID 14
#xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default,  or "off"
#xsetwacom set "Serial Wacom Tablet touch" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
#xsetwacom set "Serial Wacom Tablet touch" RawSample "2"  # data pt.s filtered, default is 2, 0-100
#xsetwacom set "Serial Wacom Tablet touch" ClickForce  # pressure, default is 27, range is 0-2047
##xsetwacom set "Serial Wacom Tablet touch" Threshold "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"  # or Relative cursor movement
#xsetwacom set "Serial Wacom Tablet touch" TapTime "250"  # default is 250 ms
#xsetwacom set "Serial Wacom Tablet touch" Button1 "1"
# sample X200t coordinates
#xsetwacom set "Serial Wacom Tablet touch" topx "48"
#xsetwacom set "Serial Wacom Tablet touch" topy "90"
#xsetwacom set "Serial Wacom Tablet touch" bottomx "915"
#xsetwacom set "Serial Wacom Tablet touch" bottomy "940"

## two finger (2FG) or multitouch
## touch = "Serial Wacom Tablet touch" = ID 14
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default,  or "off"
xsetwacom set "Serial Wacom Tablet touch" Gesture "on"  # or "off"
xsetwacom set "Serial Wacom Tablet touch" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet touch" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet touch" ClickForce  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet touch" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"  # or Relative cursor movement; is Relative needed for gestures? 
xsetwacom set "Serial Wacom Tablet touch" TapTime "250"  # default is 250 ms
xsetwacom set "Serial Wacom Tablet touch" Button1 "1"  #  needed for 2FG touch?
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 14 ZoomDistance "50"  # default is 50
xsetwacom set 14 ScrollDistance "20"  # default is 20
xsetwacom set 14 TapTime "250"  # 2FG R click, default is 250 ms
# sample X200t coordinates
#xsetwacom set "Serial Wacom Tablet touch" topx "?"
#xsetwacom set "Serial Wacom Tablet touch" topy "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomx "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomy "?"

## Developed with vfrjim
===================

```

chmod +x ~/.xsetwacom.sh
sudo sh ./xsetwacom.sh

sudo apt-get install libnotify-bin

```

Create .toggle_touch.sh (executing this script you ll be able to  activate/desactivate touchscreen using fingers) ; in /home/USER with  this content:

===================
#!/bin/bash

## Use with Lucid wacom.conf.  Get the
## "Device name" or ID number for touch
## from 'xinput --list'.  
##
## For touch state notification use:
##  sudo apt-get install libnotify-bin
## Otherwise comment (#) out the two
## notify-send lines.  If installed
## see 'man notify-send'.

TOUCH_STATE=`xsetwacom get 17 Touch`
if [ "$TOUCH_STATE" == "on" ]
  then
    echo "Touch is ON, turning OFF."
    notify-send --expire-time=1000 "Finger Touch Screen OFF"
    xsetwacom set 17 Touch off
  else
    echo "Touch is OFF, turning ON."
    notify-send --expire-time=1000 "Finger Touch Screen ON"
    xsetwacom set 17 Touch on
fi
===================

```

chmod +x ~/.toggle-touch.sh

```

REBOOT

USE YOUR FINGERPRINT :
lsusb -> to know you device

On t730 is a :
"Bus 002 Device 003: ID 08ff:2550 AuthenTec, Inc. "

Which not yet reconnized by :
[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)
nor:
[http://doc.ubuntu-fr.org/thinkfinger](http://doc.ubuntu-fr.org/thinkfinger)

(Need to wait !)

:(


Hope it worked for you !!!
I think it could be possible to improuve the .xsetwacom.sh file content in order to get more/others touchscreen gestures ...

++
seb

---

### Post by Cafe_Tony on 2011-02-21
Hello all - my very first post to UF. ZZZEB & Favux - hope I am not hijacking the thread but my problem is so similar to yours and all the relevant info is here so it seemed like a good thing to add it here. If not I apologize. 

Running lucid 10.04 on a Fujitsu ST5112 tablet / slate computer. 

Been through all the above (except setup)  and now have both the wacom.ko driver - which I now know I don't need - and the latest wacom_drv.so which is located in: /usr/lib/xorg/modules/input, along with several other drivers. 

One thing odd i noticed was that both the xorg.conf and 10-wacom.conf files were empty so I copy/pasted the wacom.conf files in via gedit. 

The problem is that the drivers won't load on re-start, at all. Tried several times and nada. Do I need to copy the wacom_drv.so into another directory? :confused:

As you can see nothing related to touch or stylus input on Xinput --list:
user@user-desktop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                               id=12    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      Kensington USB/PS2 Wheel Mouse    id=13    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9116;   &#8627; Apple Wireless Keyboard                     id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; HID 0a5c:4502                               id=11    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]

Please help - spent hours and hours on this and feeling very stupid about now. 
Thanks,

---

### Post by Favux on 2011-02-21
Hi Cafe_Tony,

Welcome to Ubuntu forums!

Could you post the 10-wacom.conf you're using?

---

### Post by Cafe_Tony on 2011-02-21
> **Favux said:**
> Hi Cafe_Tony,

Welcome to Ubuntu forums!

Could you post the 10-wacom.conf you're using?

Hi Favux, 

10-wacom.conf:
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
    Identifier "Wacom serial class identifiers"
    MatchProduct "WACf|FUJ02e5|FUJ02e7"
    Driver "wacom"
EndSection

Section "InputClass"
      Identifier "Wacom eraser class"
      MatchProduct "Wacom"
      MatchProduct "eraser"
      Option "Foo" "bar"
EndSection

Section "InputClass"
     Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
     MatchDevicePath "/dev/input/event*"
     Driver "wacom"
    Option "Button2" "3"
EndSection

---

### Post by Favux on 2011-02-21
Ok, that one has the "Wacom serial class identifiers" so you're good.  By the way the reason why compiling xf86-input-wacom didn't install the 10-wacom.conf is that Debian/Ubuntu used a hybrid 1.7 X server (backporting some early 1.8 ) so they could get rid of HAL/.fdi and go to udev/.conf.  So they have the .conf files in a non-standard location in Lucid.  In Maverick it would have installed a 50-wacom.conf in the standard location.

Is the Fujitsu ST5112 a pure slate?  I'm trying to figure out if we can re-enable the key combination to restart X.  Lot's of Fujitsu tablets report restarting X gets their digitizer working.

---

### Post by Cafe_Tony on 2011-02-21
Ok, good to know. I was concerned the .conf didn't show because the build failed. 
The 5112 is pure slate. I have access via either a bluetooth mac keyboard or onscreen virtual keyboard. 
The mac board requires re-syncing it when re-starting the machine. Also have a usb mouse. the virtual keyboard launches on start-up for now. Just in case nothing else works.

---

### Post by Favux on 2011-02-21
Alright, go to System > Preferences > Keyboard > Layouts tab > Options > Key sequence to kill X server.  Tick the box and Ctl+Alt+BackSpace should restart X again.

---

### Post by Cafe_Tony on 2011-02-21
ok, the X re-start worked (there is a new log file) and now there is a wacom line in lsmod: 

user@user-desktop:~$ lsmod
Module                  Size  Used by
wacom                  21745  0 
joydev                  8740  0 

however no functionality and no wacom module in the new xorg.0.log.

Does 10-wacom.conf need to be an executable script?

---

### Post by Favux on 2011-02-21
No.  As long as it's in /usr/lib/X11/xorg.conf.d/10-wacom.conf it should be good.

Let's look at your Xorg.0.log after a fresh boot.  It's in /var/log.  Because it's big compress it with right click Create Archive and attach it to your next post with Manage Attachments below.

---

### Post by Cafe_Tony on 2011-02-21
ok, here it is.

---

### Post by Favux on 2011-02-21
The Xorg.0.log doesn't show anything to do with your tablet in it other than fjbtndrv.  So 'xinput list' is probably blank too.  Let's see what the Xorg.0.log looks like after a X restart.  As you noted earlier the wacom.ko shouldn't have anything to do with your serial tablet, although it's interesting the module showed up after an X restart.

---

### Post by Cafe_Tony on 2011-02-21
re-started X 4 times and the xorg.0.log doesn't change. You are right about the xinput list as well. nothing about the tablet features or input devices. 

Two things from xorg.0.log got my attention: 

(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 21 23:24:31 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) [COLOR=Blue]No Layout section. [/COLOR] Using the first Screen section.
(==) [COLOR=Blue]No screen section available.[/COLOR] Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
   [COLOR=Blue] Using a default monitor configuration.[/COLOR]

And this:

(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) [COLOR=Blue]The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.[/COLOR]
(II) Loader magic: 0x81f0e80

Could i need to reconfigure udev?

---

### Post by Favux on 2011-02-22
Well I think the Match Product line with FUJ02e5|FUJ02e7 covers all of the current Fujitsu ISDV4 devices (tablet PCs).  By the way the *Option "ForceDevice" "ISDV4"* line has been deprecated starting with xf86-input-wacom-0.10.8.

Almost all of the ISDV4 devices use the /ttyS0 port.  We could check and see if raw data is coming over that port with xxd or evtest.

At this point I'm hoping something went wrong with your cloning of the xf86-input-wacom git repository.  Why don't you try recloning it or use the 0.10.11 tar:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

The root problem is the Fujitsu version of the Wacom digitizers for serial tablet PCs apparently doesn't quite use the vanilla Wacom ISDV4 protocol.  Once they're initialized they seem OK.  So the difference between the two protocols may be as little as one bit in the initialization sequence.  But as far as I know, no one has figured out what the difference is.

---

### Post by Cafe_Tony on 2011-02-22
I reinstalled last night. No difference. Used the tar pkg. Will be offline till this wve. Will check in tjen. Thx!

---

### Post by Cafe_Tony on 2011-02-22
Ok so to update, I re-installed the xf86 from the tar pkg last night and no change. I'm running the evdev module of xorg, could that be inhibiting some driver installs? I was going to remove it and see but to do so means it removes all xorg. 
Does Maverick have tablet support?

---

### Post by Favux on 2011-02-22
Right, don't remove xorg.  Evdev shouldn't interfere with touch.  The Synaptic touchpad driver used to but they fixed that.  Speaking of xorg make sure you didn't remove xserver-xorg-input-all at some point.  xf86-input-wacom needs that installed to work.

---

### Post by Cafe_Tony on 2011-02-22
Ok, progress. Went into package manager to make sure all the xorg bits still there and now xserver-input-wacom is there. It wasn't before. So installed it and now i get some wacom lines in xinput and xorg.0.log (see below) but nothing I recognize as tablet related in lsmod. Also, the stylus still doesn't do anything. 

user@user-desktop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                               id=12    [slave  pointer  (2)]
&#9116;   &#8627; Apple Wireless Keyboard                     id=13    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      Kensington USB/PS2 Wheel Mouse    id=14    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=19    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=20    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; HID 0a5c:4502                               id=11    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=16    [slave  keyboard (3)]

excerpt from xorg.0.log:

(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24576 maxY=18432 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540

---

### Post by Favux on 2011-02-22
Good, progress.

Let me explain further.  Starting with Karmic they introduced a new dependency between xserver-xorg-input-all and xserver-xorg-input-wacom.  You can't install one without installing the other.   And you can't uninstall one without uninstalling the other.  And xserver-xorg-input-wacom (the xf86-input-wacom package starting in Lucid) requires xserver-xorg-input-all to work.

What you've done by installing xserver-xorg-input-wacom is to install the default xf86-input-wacom 0.10.8 over the compiled one.  But since it has xserver-xorg-input-all it is now "working".  Your tablet is detected as a serial tablet in xinput.

We don't care if we don't see 'wacom', the wacom.ko, in the lsmod output because that is the usb kernel driver and your serial tablet does not need it.

Now if an X restart doesn't initialize the serial digitizer then your option is to recompile xf86-input-wacom over the default xf86-input-wacom.  Don't try to uinstall the default.  Hopefully some of the support they added for the Fujitsu's is what you need to get it working.

---

### Post by Cafe_Tony on 2011-02-22
I recompiled the xf86-wacom to the latest package. Now the new driver is launching and stylus and eraser show up in xinput but not the tablet. Also checked to see if I had all the updates. 

user@user-desktop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                               id=12    [slave  pointer  (2)]
&#9116;   &#8627; Apple Wireless Keyboard                     id=13    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      Kensington USB/PS2 Wheel Mouse    id=14    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=19    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=20    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; HID 0a5c:4502                               id=11    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=16    [slave  keyboard (3)]


from xorg0.log

(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.11
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Serial Wacom Tablet: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(II) Serial Wacom Tablet stylus: serial tablet id 0x90.
(--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
(--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) Serial Wacom Tablet stylus: hotplugging dependent devices.
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "19200"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=100000 resol Y=100000
(**) Option "BaudRate" "19200"
(II) Serial Wacom Tablet stylus: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
(--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=100000 resol Y=100000

---

### Post by Favux on 2011-02-23
Geez.  From those outputs it sure seems like everything is setting up correctly and it should work.

I'm stumped.

Time to post to linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

I may be missing or ignorant of the obvious.

---

### Post by Cafe_Tony on 2011-02-23
You mentioned earlier we could run xxd or evtest to check for data? Should I try that?

---

### Post by Favux on 2011-02-23
That's definitely worth doing.  Use: 

xxd /dev/ttyS0

xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.

---

### Post by Cafe_Tony on 2011-02-23
ok, that's not good. SO and S3 ran but no input from the pen/screen.  Also, I was surfing the forums looking for more ideas and checked my dev/input directory and there's nothing there related to tablet, stylus wacom, etc. Even the list by event number doesn't include anyting over 16. (the tablet devices are devices 17>19)

---

### Post by Favux on 2011-02-23
Hmmm.  I'm not sure if xxd didn't work because the wacom X driver puts an EVIOCGRAB on the device file when the device is enabled now. Once the grab is established, only a single process (the X server) will receive events from that device.  So that might be a problem,

Let's try evtest.  To get around the grab enter a virtual terminal by using Ctrl+Alt+F1.  When there run:

sudo evtest /dev/ttyS0 etc.

and move the stylus around on the screen.  To get back to X, press Ctrl+Alt+F7.

---

### Post by Cafe_Tony on 2011-02-24
Wasn't able to run evtest. Kept getting a not found error. 

Been reviewing your How To post and found that my 69-xserver-xorg-input-wacom.rules file is empty. Do I need that since I'm using the 10-wacom.conf not the xorg.conf? 
Should I try using xorg.conf (which is also blank) instead?

---

### Post by Favux on 2011-02-24
Ok, not installed in Lucid by default.  Try *apt-get install evtest*.  That may not work if it comes in another package.  But it should tell you what package it is in.

The wacom.rules are basically so you have a symlink available to use in xorg.conf.  You shouldn't need an xorg.conf.  The wacom.conf in xorg.conf.d should work for you.  I suppose it's something to consider/try as a last resort but I doubt it would make a difference.

---

### Post by Cafe_Tony on 2011-02-24
l installed a few days ago. the error is file not found. Thanks for all your help and time. i need a working machine and it seems clear at this point linux isn't going to work w/ fujitsu. Frankly after all the hype proclaiming lucid as consumer friendly l'm shocked at how inadequate it is as a working os. Consumers don't want nor are they equipped to do constant / endless debugging.  Again, i do appreciate all your effort so please don't think my frustration means otherwise.  T~

---

### Post by Favux on 2011-03-02
Hi Cafe_Tony,

That's not Ubuntu's fault.  The linux wacom project is in charge of the Wacom drivers, not Ubuntu.

I was mistaken and forgot a Fujitsu product ID that was recently supported by the linux wacom project.  So the match line in the 50-wacom.conf should be:
```
MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02E9"
```
The FUJ02E9 is described as having a stylus and one finger touch (1FGT).  If that describes the Fujitsu ST5112 tablet/slate, that's likely what we were missing and what you need to get it working.

---

### Post by Cafe_Tony on 2011-03-05
thanks for this. i'm traveling the next week / 2 and will try it when i get back and update you.
thanks

---

### Post by Cobuntu on 2011-03-06
Just got a new T730 and thanx to [zzzeb]("http://ubuntuforums.org/member.php?u=1217884") I was able to get Single Finger Touch + Pen working in 10.10. I also tried 11.04 alpha3 and it worked out of the box.
But how about multitouch - or at least 2 fingers. Has anyone info on that? 

On a sidemark: This was the only discussion I found about the T730 so I think it is not a good idea to discuss another model in here.

---

### Post by Cobuntu on 2011-03-07
OK, I helped myself. As I had problems with my Gobi UMTS Modem that I could not solve within 10.10 I tried 11.04 alpha 3 instead (so I don't know about 10.10 it but should be the same or similar). Gobi works in there with the copied Windows firmware and gobi-loader.
Also Pen and Single touch works out of the box, gestures are already there, you just have to turn them on. I figured it out with the help of these posts: 
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/678100](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/678100) #2
   	 	 	 	  #4 [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/678100](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/678100)
   	 	 	 	   [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1515562](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1515562)

All I needed to do in 11.04 is: xsetwacom set "Serial Wacom Tablet touch" Gesture "on"
To have it autostart I did:
> downloaded the .xsetwacom.sh from the last post.
> replaced content by the following two lines:
## touch = ID 17 = "Serial Wacom Tablet touch" 
xsetwacom set "Serial Wacom Tablet touch" Gesture "on"
> renamed it to .xsetwacom.sh and placed it in my home directory (it is a hidden file!)
> made it executable via terminal:
chmod +x ~/.xsetwacom.sh
> System->Preferences->Startup Applications: add wiith command "sh /home/yourusername/.xsetwacom.sh"
> REBOOT and try out scrolling with two fingers, it works

---

