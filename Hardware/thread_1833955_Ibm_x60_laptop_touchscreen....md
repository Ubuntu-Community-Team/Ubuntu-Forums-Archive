---
title: "Ibm x60 laptop touchscreen..."
date: 2011-08-26
forum: Hardware
---

### Post by Firezap on 2011-08-26
Hi all. I just got a ibm X60 tablet and it runs very smoothly with Xubuntu 11.04. Sadly when I bought this computer it was missing it's stylus but I think it has finger touch as well. In fact if I go to the mouse settings it recognizes "Serial Wacom input touch'...Which sounds promising. I have found examples were people got the stylus working but not finger touch. Any help would be greatly appreciated.8)

---

### Post by Favux on 2011-08-26
Hi Firezap,

You should be able to get a stylus from Lenovo or maybe Wacom for about $10.

I don't remember if some X60t's had touch or not.  What is the output of *xinput list* in a terminal?

---

### Post by Firezap on 2011-08-26
I get...
usage :
    xinput get-feedbacks <device name>
    xinput set-ptr-feedback <device name> <threshold> <num> <denom>
    xinput set-integer-feedback <device name> <feedback id> <value>
    xinput get-button-map <device name>
    xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
    xinput set-pointer <device name> [<x index> <y index>]
    xinput set-mode <device name> ABSOLUTE|RELATIVE
    xinput list [--short || --long] [<device name>...]
    xinput query-state <device name>
    xinput test [-proximity] <device name>
    xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>]
    xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>]
    xinput reattach <id> <master>
    xinput float <id>
    xinput set-cp <window> <device>
    xinput test-xi2 <device>
    xinput list-props <device> [<device> ...]
    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
    xinput set-float-prop <device> <property> <val> [<val> ...]
    xinput set-atom-prop <device> <property> <val> [<val> ...]
    xinput watch-props <device>
    xinput delete-prop <device> <property>
    xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]


I put my old hardrive in that had Ubuntu 9.04 in it and the touch screen worked...Although it needed calibrated but it worked fine.

---

### Post by cmstackar on 2011-08-26
You might want to try this:
[http://www.thinkwiki.org/wiki/How_to_install_MultiTouch_from_source](http://www.thinkwiki.org/wiki/How_to_install_MultiTouch_from_source)

---

### Post by Favux on 2011-08-26
Good, so you have touch.  I'm pretty sure the X60t only has 1FGT not 2FGT, so multi-touch for the Wacom digitizer doesn't enter in it.  Besides that's very old and you do not want to use a xorg.conf.

The command you want to enter into the terminal is:
```
xinput list
```

---

### Post by Firezap on 2011-08-26
Sorry, here it is...
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=11    [slave  keyboard (3)]
Thanks for the replies.

---

### Post by Firezap on 2011-08-26
It started working...and I do not even know what I did exactly...But it needs calibrated. Any good way to do that?

I rebooted the computer and it does not work at all again.

---

### Post by Favux on 2011-08-26
Great!  I was going to suggest we try using a xsetwacom set command to turn touch on:
```
xsetwacom set "Serial Wacom Tablet touch" Touch on
```
That should be the default set by the xf86-input-wacom X driver, but it seems like a few ISDV4 serial tablet PCs need that in Natty for some reason.

You can calibrate with xinput_calibrator which is called xinput-calibrator in Natty's Universe repository.  Then once you get the coordinates you can use xsetwacom commands for that, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration).  I also have a sample xsetwacom.sh for the X61t which should work for the X60t in post #2 on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Be sure to check part IV. because the xsetwacom parameter names change depending on the version of xf86-input-wacom you have:
```
xsetwacom -V
```

---

### Post by Firezap on 2011-08-27
Thanks. Although I am having a little trouble calibrating it. And every time I restart the computer the touch turns of again lol.](*,)
I am also having trouble getting in the numbers...Now my touchscreen is really off....
I look at your file and this is for the tablet touch input...
## Remove comments if your X61t has touch
## touch = ID 15 = "Serial Wacom Tablet touch"
#xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default,  or "off"
#xsetwacom set "Serial Wacom Tablet touch" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
#xsetwacom set "Serial Wacom Tablet touch" RawSample "2"  # data pt.s filtered, default is 2, 0-100
#xsetwacom set 15 ClickForce "27"  # pressure, default is 27, range is 0-2047
##xsetwacom set 15 Threshold "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set 15 Mode "Absolute"  # or Relative cursor movement
#xsetwacom set 15 TapTime "250"  # default is 250 ms
#xsetwacom set 15 Button1 "1"
# sample X61t coordinates
#xsetwacom set 13 topx "?"
#xsetwacom set 13 topy "?"
#xsetwacom set 13 bottomx "?"
#xsetwacom set 13 bottomy "?"

I do not see the coordinates...And when I enter the ones I made from attempting to calibrate my screen early the mouse instantly jumps to the bottom  of the screen. Grrrr lol
Any advice? I am not very familiar with this lol.

---

### Post by Firezap on 2011-08-27
Sorry about bumping this but I really would like to figure this out....:confused:

---

### Post by Favux on 2011-08-27
For you with xf86-input-wacom-0.10.11 it should look something like:
```
## Remove comments if your X60t has touch
## touch = ID 13 = "Serial Wacom Tablet touch"
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default, or "off"
#xsetwacom set "Serial Wacom Tablet touch" Suppress "2" # data pt.s trimmed, default is 2, 0-100
#xsetwacom set "Serial Wacom Tablet touch" RawSample "4" # data pt.s filtered, default is 4, 1-20
#xsetwacom set "Serial Wacom Tablet touch" Threshold "27" # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute" # or Relative cursor movement
#xsetwacom set "Serial Wacom Tablet touch" TapTime "250" # default is 250 ms
#xsetwacom set "Serial Wacom Tablet touch" Button 1 "1"
## sample X60t coordinates
xsetwacom set "Serial Wacom Tablet touch" Area x1 y1 x2 y2
```
Since you didn't post coordinates from xinput_calibrator I can't add them.  Likely the driver default coordinates are in your Xorg.0.log in /var/log.  Just search 'Wacom' or 'touch'.

---

### Post by Firezap on 2011-08-27
Here is the log...
[    15.635] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[    15.635] (II) Using input driver 'wacom' for 'Serial Wacom Tablet touch'
[    15.635] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    15.635] (**) Serial Wacom Tablet touch: always reports core events
[    15.635] (**) Option "Device" "/dev/ttyS4"
[    15.635] (**) Option "BaudRate" "38400"
[    15.635] (**) Option "StopBits" "1"
[    15.635] (**) Option "DataBits" "8"
[    15.635] (**) Option "Parity" "None"
[    15.635] (**) Option "Vmin" "1"
[    15.635] (**) Option "Vtime" "10"
[    15.635] (**) Option "FlowControl" "Xoff"
[    15.635] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=24576 maxY=18432 maxZ=127 resX=100000 resY=100000  tilt=disabled
[    15.635] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0b/tty/ttyS4"
[    15.635] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
[    15.636] (--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=1024 bottom Y=1024 resol X=0 resol Y=0
[    15.636] (**) Serial Wacom Tablet touch: (accel) keeping acceleration scheme 1
[    15.636] (**) Serial Wacom Tablet touch: (accel) acceleration profile 0
[    15.636] (**) Serial Wacom Tablet touch: (accel) acceleration factor: 2.000
[    15.636] (**) Serial Wacom Tablet touch: (accel) acceleration threshold: 4
[    15.636] (II) Serial Wacom Tablet stylus: hotplugging completed.

Sorry, I have never messed with this stuff much...The hardest thing I ever did was configure wizardpen and that was a long time ago lol.

---

### Post by Favux on 2011-08-27
Don't worry about it.  This is a lot of information to take in at once.  As you get a little more familiar with it it will get easier.

Alright, according to:
```
[ 15.636] (--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=1024 bottom Y=1024 resol X=0 resol Y=0
```
it should be:
```
## Remove comments if your X60t has touch
## touch = ID 13 = "Serial Wacom Tablet touch"
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default, or "off"
#xsetwacom set "Serial Wacom Tablet touch" Suppress "4" # data pt.s trimmed, default is 2, 0-100
#xsetwacom set "Serial Wacom Tablet touch" RawSample "4" # data pt.s filtered, default is 4, 1-20
#xsetwacom set "Serial Wacom Tablet touch" Threshold "27" # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute" # or Relative cursor movement
#xsetwacom set "Serial Wacom Tablet touch" TapTime "250" # default is 250 ms
#xsetwacom set "Serial Wacom Tablet touch" Button 1 "1"
## sample X60t coordinates
xsetwacom set "Serial Wacom Tablet touch" Area 0 0 1024 1024
```
Notice the stylus and touch have different sizes.  That's because they are in fact two separate devices sandwiched together with the LCD.  And of course touch has a much lower resolution.  Although I have to admit those are suspiciously square coordinates.

And the Xorg.0.log excerpt was useful because I learned the serial port in play was ttyS4.  I would have guessed ttyS0.

---

### Post by Firezap on 2011-08-27
Thanks for the info, I am sort of lost what to do next though lol. Your helping me a great deal though, thank you.

---

### Post by Favux on 2011-08-27
Well, if you haven't already you now want to install it as a start up script.  See ***IV. Use of a xsetwacom script file*** in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") for instructions.

---

### Post by Firezap on 2011-08-28
Well, the script works. But the calibration is still goofed up. It seems to work in the middle but you can not reach the edges of the screen.:mad: So I ran the calibration tool thing lol, and got...
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "!!Name_Of_TouchScreen!!"
    Option    "MinX"    "442"
    Option    "MaxX"    "22922"
    Option    "MinY"    "1162"
    Option    "MaxY"    "17594"
EndSection
Sooo, I am playing with these numbers, I feel I am close.:)

It just hit me that these numbers are way to large lol....
xsetwacom set "Serial Wacom Tablet touch" Area -50 50 1024 1024 lets me get to the top of the screen fine, it gets me close to the bottom but not all the way. I also can not touch the sides....I will try again soon lol.

---

### Post by Favux on 2011-08-28
The xsetwacom command basically looks good.  Just need to fine tune the coordinates.  The nice thing about xsetwacom commands is they apply as soon as you enter them so you don't need to keep restarting.

Are you specifying for xinput_calibrator the touch device?  If it is not able to calibrate both the stylus and touch you'll have to do it manually.  

You already have the "device name" from *xinput list*.  To see the manual for it just enter *man xinput_calibrator* in a terminal.

---

### Post by Firezap on 2011-08-28
This seems to work almost perfectly...

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

## Remove comments if your X60t has touch
## touch = ID 13 = "Serial Wacom Tablet touch"
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default, or "off"
#xsetwacom set "Serial Wacom Tablet touch" Suppress "4" # data pt.s trimmed, default is 2, 0-100
#xsetwacom set "Serial Wacom Tablet touch" RawSample "4" # data pt.s filtered, default is 4, 1-20
#xsetwacom set "Serial Wacom Tablet touch" Threshold "27" # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute" # or Relative cursor movement
#xsetwacom set "Serial Wacom Tablet touch" TapTime "250" # default is 250 ms
#xsetwacom set "Serial Wacom Tablet touch" Button 1 "1"
## sample X60t coordinates
xsetwacom set "Serial Wacom Tablet touch" Area 25 50 950 980
## Developed with dr4ziw and iRi_E


Thank you for all your help! Set the comp to boot it up on startup and it works great!!!!! Thanks.:guitar:
Maybe this will help people in the future with the same x60 issue lol.

---

### Post by Favux on 2011-08-28
Great!  Nice work.  :D

---

### Post by Firezap on 2012-02-09
I forgot to mention, this proccess also worked just fine for me with Ubuntu 11.10.;)

---

