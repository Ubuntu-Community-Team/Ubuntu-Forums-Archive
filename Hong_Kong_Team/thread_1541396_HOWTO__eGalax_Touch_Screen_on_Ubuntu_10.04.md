---
title: "HOWTO : eGalax Touch Screen on Ubuntu 10.04"
date: 2010-07-29
forum: Hong Kong Team
---

### Post by samiux on 2010-07-29
I have a Gigabyte TouchNote T1028X that comes with Intel Atom N280 and eGalax Touch Screen.  It runs Ubuntu 10.04 flawlessly except touchpad and touchscreen.

Hereby, I wrote a tutorial to overcome these problems.  [Here you are]("http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html").

By the way, if there is any touch screen laptop or netbook that not using eGalax, please report here and also attach the printout of "lsusb".  Maybe I can give a hand to solve the problem.  

Or, anyone's touch screen devices can run Ubuntu 10.04 perfectly, please also report here with the result of "lsusb" and the brand name, model as well as the howto.

Samiux

---

### Post by jayune on 2010-08-20
ok please i need a little help i follow your instruction and its not working no finger inputs at all and wen ever i try to run the calibration tool it "saysroot@jayune-laptop:~/Downloads/tias-xinput_calibrator-6836b99# xinput_calibratorError: No calibratable devices found." now i dont have the gigabyte touch note so that might be it but the result of my lsusb is 



Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51e Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 046e:3002 Behavior Tech. Computer Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by samiux on 2010-08-20
> **jayune said:**
> ok please i need a little help i follow your instruction and its not working no finger inputs at all and wen ever i try to run the calibration tool it "saysroot@jayune-laptop:~/Downloads/tias-xinput_calibrator-6836b99# xinput_calibratorError: No calibratable devices found." now i dont have the gigabyte touch note so that might be it but the result of my lsusb is 



Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51e Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 046e:3002 Behavior Tech. Computer Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Did you complete the Step 1?  Your system is required to reboot after doing the Step 1.


```
Step 1 :

sudo nano /etc/default/grub

Append "i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40" to "GRUB_CMDLINE_LINUX_DEFAULT".

*where i8042.noloop=1 solves the touchpad probem.

It will look like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"

Save and exit.

sudo update-grub


```

Samiux

---

### Post by jayune on 2010-08-22
yep i did everything but touch isnt being recognized i guess ill redo ubuntu cause ive been trying a lot of steps before this one, i even tried your step for 9.10 before discovering this so ill let you know

---

### Post by jayune on 2010-08-23
ok i just had an idea......so your step at some point backlist the default usbtouch driver but if there no driver the touch screen wont be recognized so what i did was go strait to the xinput install it works butim getting this message so can you help me a bit


    Setting new calibration data: 71, 2016, 1929, 148


== Saving the calibration ==
If you have the 'xinput' tool installed, a simple way is to create a script that starts with your X session, containing the following command(s):
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 71 2016 1929 148
See scripts/xinput_calibrator_pointercal.sh for an example used on mobile devices

If you have evdev version 2.3.0 or higher, there are 2 more ways: the tranditional way (xorg.conf) and the new way (udev rule):
xorg.conf: edit /etc/X11/xorg.conf and add in the 'Section "InputDevice"' of your device:
    Option    "Calibration"        "71 2016 1929 148"
udev rule: create the file '/etc/udev/rules.d/99_touchscreen.rules' with:
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="eGalax Inc. USB TouchController", GOTO="xorg_touchscreen_end"
    ENV{x11_options.calibration}="71 2016 1929 148"
    LABEL="xorg_touchscreen_end"

i dont really get it

---

### Post by jayune on 2010-08-23
ok i just had an idea......so your step at some point backlist the default usbtouch driver but if there no driver the touch screen wont be recognized so what i did was go strait to the xinput install it works butim getting this message so can you help me a bit


    Setting new calibration data: 71, 2016, 1929, 148


== Saving the calibration ==
If you have the 'xinput' tool installed, a simple way is to create a script that starts with your X session, containing the following command(s):
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 71 2016 1929 148
See scripts/xinput_calibrator_pointercal.sh for an example used on mobile devices

If you have evdev version 2.3.0 or higher, there are 2 more ways: the tranditional way (xorg.conf) and the new way (udev rule):
xorg.conf: edit /etc/X11/xorg.conf and add in the 'Section "InputDevice"' of your device:
    Option    "Calibration"        "71 2016 1929 148"
udev rule: create the file '/etc/udev/rules.d/99_touchscreen.rules' with:
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="eGalax Inc. USB TouchController", GOTO="xorg_touchscreen_end"
    ENV{x11_options.calibration}="71 2016 1929 148"
    LABEL="xorg_touchscreen_end"

i dont really get it

---

### Post by samiux on 2010-08-23
> **jayune said:**
> ok i just had an idea......so your step at some point backlist the default usbtouch driver but if there no driver the touch screen wont be recognized so what i did was go strait to the xinput install it works butim getting this message so can you help me a bit


    Setting new calibration data: 71, 2016, 1929, 148


== Saving the calibration ==
If you have the 'xinput' tool installed, a simple way is to create a script that starts with your X session, containing the following command(s):
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 71 2016 1929 148
See scripts/xinput_calibrator_pointercal.sh for an example used on mobile devices

If you have evdev version 2.3.0 or higher, there are 2 more ways: the tranditional way (xorg.conf) and the new way (udev rule):
xorg.conf: edit /etc/X11/xorg.conf and add in the 'Section "InputDevice"' of your device:
    Option    "Calibration"        "71 2016 1929 148"
udev rule: create the file '/etc/udev/rules.d/99_touchscreen.rules' with:
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="eGalax Inc. USB TouchController", GOTO="xorg_touchscreen_end"
    ENV{x11_options.calibration}="71 2016 1929 148"
    LABEL="xorg_touchscreen_end"

i dont really get it

For Ubuntu 9.10, please refer to [this tutorial]("http://samiux.blogspot.com/2009/12/howto-ubuntu-910-on-gigabyte-t1028x.html").

---

### Post by RockoRobotics on 2010-09-04
I'm following your tutorial and when I get to the calibration step, the computer seems to know it is calibrating an eGalax touchscreen, but the computer does not respond to the touchscreen.  Is there some other test I can perform to see if the Touchscreen is sending data to the computer?  What about a test to see if the driver is functioning correctly?

---

### Post by samiux on 2010-09-04
> **RockoRobotics said:**
> I'm following your tutorial and when I get to the calibration step, the computer seems to know it is calibrating an eGalax touchscreen, but the computer does not respond to the touchscreen.  Is there some other test I can perform to see if the Touchscreen is sending data to the computer?  What about a test to see if the driver is functioning correctly?

If I understand correctly, you need to hold the pen on the screen for a while (until the circle goes around) at calibration.  Please read the instruction on the screen carefully when the calibration begins.

---

### Post by RockoRobotics on 2010-09-11
I just checked the calibration program.  It says to simply press the point.  If it does not detect a press by the time the circle moves around, then it aborts.

I'm currently working with the place where I purchased the touch screen to get some replacement parts sent out since I have had the same problem on a Windows 7 machine.

---

### Post by sansbury on 2010-09-15
Hi, the HOWTO helped me get my touchscreen *ALMOST* working. It still needs calibration, but the motion is smooth, the problem is that the Y axis is reversed. If I move up, the pointer goes down, and vice-versa. The X axis works properly. I am using a no-name touchscreen. lsusb reports it as follows: 

Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

ADD: I tried calibrating it, and the calibration ran successfully. It gave me a line like this:

xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" 32 93 1926 1854 156

If I run that in a terminal, then the screen works properly in all ways. However, if I reboot, obviously, it loses the configuration. In order to get the screen working properly, I have to run the calibration tool and then execute the command again. If I just execute the same command without running the calibration process, it does not work. Is there any way to make this calibration permanent?

---

### Post by samiux on 2010-09-16
> **sansbury said:**
> Hi, the HOWTO helped me get my touchscreen *ALMOST* working. It still needs calibration, but the motion is smooth, the problem is that the Y axis is reversed. If I move up, the pointer goes down, and vice-versa. The X axis works properly. I am using a no-name touchscreen. lsusb reports it as follows: 

Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

ADD: I tried calibrating it, and the calibration ran successfully. It gave me a line like this:

xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" 32 93 1926 1854 156

If I run that in a terminal, then the screen works properly in all ways. However, if I reboot, obviously, it loses the configuration. In order to get the screen working properly, I have to run the calibration tool and then execute the command again. If I just execute the same command without running the calibration process, it does not work. Is there any way to make this calibration permanent?

Please refer to "Step 3" where Option "Calibration" should be "93 1926 1854 156".

---

### Post by sansbury on 2010-09-16
Thanks! That worked perfectly.

---

### Post by twotwenty on 2010-09-29
when I use xinput_calibrator I get output:

Warning: multiple calibratable devices found, calibrating last one (eGalax Inc. Touch)
use --device to select another one.
Calibrating EVDEV driver for "eGalax Inc. Touch" id=11
current calibration values (from XInput): min_x=0, max_x=2047 and min_y=0, max_y=2047

Doing dynamic recalibration:
Swapping X and Y axis...
Setting new calibration data: 97, 1938, 1908, 116


--> Making the calibration permanent <--
Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" 32 97 1938 1908 116
xinput set-int-prop "eGalax Inc. Touch" "Evdev Axes Swap" 8 1



after doing this the axis to the cursor are reversed left going right up going down, when I run xinput_calibrator a second time  output:


Warning: multiple calibratable devices found, calibrating last one (eGalax Inc. Touch)
use --device to select another one.
Calibrating EVDEV driver for "eGalax Inc. Touch" id=11
current calibration values (from XInput): min_x=97, max_x=1938 and min_y=1908, max_y=116

Doing dynamic recalibration:
Setting new calibration data: 1929, 95, 125, 1901


--> Making the calibration permanent <--
Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" 32 1929 95 125 1901



at this point everything works fine until reboot 

if I edit the rule 05-evdev.conf and stick in the second outputs values "32 1929 95 125 1901" and reboot, the cursor goes to the top right or completely vanishes, running the calibrator again will not finish it takes the first input and does not register any others

I have also tried swap axes on with no avail jsut more wierdness and not able to complete the calibrator

---

### Post by twotwenty on 2010-09-29
well I figured this one out after a little more trial and error and a bit of man page reading 

turns out there is more then SwapAxes there is also InvertX and Y
for anyone having some strange issues its another option to mess with.

also the first number giving in a 5 number set from xinput_calibrator is for soemthing I dont understand 

since the man page only calls for 4 values min/max X and min/max Y so I snipped off the 32 from my calibration

the xinput_calibration setting I got my variables from is 

[B]xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" 32 97 1938 1908 116
xinput set-int-prop "eGalax Inc. Touch" "Evdev Axes Swap" 8 1 [/B]

this is what my final evdev rule looks like 

[B]
Section "InputClass"
Identifier "eGalax"
MatchProduct "eGalax"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
Option "SwapAxes" "yes"
Option "InvertX" "1"
Option "InvertY" "1"
Option "Calibration" "xinput set-int-prop "eGalax Inc. Touch" "Evdev Axis Calibration" "97 1938 1908 116"[/B]

---

### Post by Muzafsh on 2010-12-17
Hello Samiux,

I am running Ubuntu 10.10 on the system
to start with it did not carry a touchscreen feature out of the box !!!

BTW My lsusb result:
> =============================================================
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1199:0220 Sierra Wireless, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1bcf:05ca Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 006: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
============================================================


I came across your post here

[http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html")


I followed the steps there and the touchscreen option showed up in the menu System->Administration->Calibrate Touchscreen.

I however installed xinput-calibrator as per your steps from the above post.

To calibrate i ran the following command as advised

'sudo xinput_calibrator'

I got the calibration screen, i calibrated it with a stylus for accuracy.

I got the following instructions...
> 
Warning: multiple calibratable devices found, calibrating last one (eGalax Inc. Touch)
	use --device to select another one.
Calibrating EVDEV driver for "eGalax Inc. Touch" id=13
	current calibration values (from XInput): min_x=0, max_x=2047 and min_y=0, max_y=2047

Doing dynamic recalibration:
	Swapping X and Y axis...
	Setting new calibration data: 1947, 137, 139, 1755


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"eGalax Inc. Touch"
	Option	"Calibration"	"1947 137 139 1755"
	Option	"SwapAxes"	"1"
EndSection


When i tested my touchscreen, every time i touched a point on the screen the cursor would move to the opposite side of the screen instead of at the point i touched, seems like the axis's had gotten swapped

I ran the calibration a second time...
& I got the following second set of instructions...
> 
Warning: multiple calibratable devices found, calibrating last one (eGalax Inc. Touch)
	use --device to select another one.
Calibrating EVDEV driver for "eGalax Inc. Touch" id=13
	current calibration values (from XInput): min_x=1947, max_x=137 and min_y=139, max_y=1755

Doing dynamic recalibration:
	Setting new calibration data: 139, 1949, 1750, 134


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"eGalax Inc. Touch"
	Option	"Calibration"	"139 1949 1750 134"
EndSection



After running the second calibration my response got corrected and i could use my touch screen without any problem as a touch mouse.

However this calibration results were valid only for the current login session, and when the system was restarted the calibration was gone.

[B]Can You Please Help Me Calibrate My Touchscreen Permanantly ???

Also can you please guide me to enable the automatic right-click option [/B]


However my touch screen can be used only as a touch mouse.

[B]A complete Tablet Touch Function was still elusive  :(

Is there any way a Tablet Touch function be achieved on this touch screen on Ubuntu 10.10?

I would love to see my touch screen perform the page flicks easily and greatly enhance my overall touch screen experience as close to a real Tablet touchscreen.[/B]

thanks in advance !!!

---

### Post by samiux on 2010-12-17
> **Muzafsh said:**
> Hello Samiux,

I am running Ubuntu 10.10 on the system
to start with it did not carry a touchscreen feature out of the box !!!

BTW My lsusb result:



I came across your post here

[http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html")


I followed the steps there and the touchscreen option showed up in the menu System->Administration->Calibrate Touchscreen.

I however installed xinput-calibrator as per your steps from the above post.

To calibrate i ran the following command as advised

'sudo xinput_calibrator'

I got the calibration screen, i calibrated it with a stylus for accuracy.

I got the following instructions...


When i tested my touchscreen, every time i touched a point on the screen the cursor would move to the opposite side of the screen instead of at the point i touched, seems like the axis's had gotten swapped

I ran the calibration a second time...
& I got the following second set of instructions...



After running the second calibration my response got corrected and i could use my touch screen without any problem as a touch mouse.

However this calibration results were valid only for the current login session, and when the system was restarted the calibration was gone.

[B]Can You Please Help Me Calibrate My Touchscreen Permanantly ???

Also can you please guide me to enable the automatic right-click option [/B]


However my touch screen can be used only as a touch mouse.

[B]A complete Tablet Touch Function was still elusive  :(

Is there any way a Tablet Touch function be achieved on this touch screen on Ubuntu 10.10?

I would love to see my touch screen perform the page flicks easily and greatly enhance my overall touch screen experience as close to a real Tablet touchscreen.[/B]

thanks in advance !!!

Muzafsh,

Did you follow every step as per my [tutorial]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html")?

For right-click, you should press the mouse pad's right-click button at the same time.

---

### Post by Muzafsh on 2010-12-18
Yes every step as you mentioned.
But the calibration is just not permanent.
help greatly appreciated.
thanks

---

### Post by miegiel on 2010-12-18
> **Muzafsh said:**
> Yes every step as you mentioned.
But the calibration is just not permanent.
help greatly appreciated.
thanks

I use this line in a script that automatically runs as I log into X (works in a terminal too).
```
xinput --set-prop --type=int --format=32 "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 6 4086 0 4092
```
You'll need to use your own calibration values.

---

### Post by samiux on 2010-12-18
> **Muzafsh said:**
> Yes every step as you mentioned.
But the calibration is just not permanent.
help greatly appreciated.
thanks

Please double check "Step 3" to see if something missing.  Please use your value instead of mine.

---

### Post by Muzafsh on 2010-12-26
Thanks people, issue resolved

did the following...

Created the following file...
/etc/X11/xorg.conf.d/99-calibration.conf

and pasted the following set of snippets that threw up after calibration.

----------------------------------
Section "InputClass"
Identifier	"calibration"
MatchProduct	"eGalax Inc. Touch"
Option	"Calibration"	"1947 137 139 1755"
Option	"SwapAxes"	"1"
EndSection

Section "InputClass"
Identifier	"calibration"
MatchProduct	"eGalax Inc. Touch"
Option	"Calibration"	"139 1949 1750 134"
EndSection
----------------------------------

and Wallah !!! my calibration got set permanently

:)

---

### Post by Muzafsh on 2010-12-26
Now looking forward to the following...

1. 'right-click function'.
2. the ever elusive 'flick function'.

---

### Post by Mr P.S on 2011-01-16
Hello.
 I have followed all the steps in your Wiki.
 When I restart the computer and try calibrate touchscreen.
 Do I get error message:No calibratable devices found
and the computer does not respond to the touchscreen
 Restore my computer to remove the changes that were made according to your Wiki.
 Can I calibrate the touchscreen.
 But after reboot I have to do a new calibration.

---

### Post by samiux on 2011-01-17
> **Mr P.S said:**
> Hello.
 I have followed all the steps in your Wiki.
 When I restart the computer and try calibrate touchscreen.
 Do I get error message:No calibratable devices found
and the computer does not respond to the touchscreen
 Restore my computer to remove the changes that were made according to your Wiki.
 Can I calibrate the touchscreen.
 But after reboot I have to do a new calibration.

Checklist :

(1) Do you using Ubuntu 10.10 or 10.04?  If you are using Ubuntu 10.10, please refer to this [link]("http://ubuntuforums.org/showthread.php?t=1613000").
(2) Do you follow all the steps of the tutorial?
(3) Does your Touch Screen device is eGalax and the Device ID is the same as the tutorial?

Samiux

P.S. the program name for calibration is changed to "xinput_calibrator".

---

### Post by Mr P.S on 2011-01-18
> **samiux said:**
> Checklist :

(1) Do you using Ubuntu 10.10 or 10.04?  If you are using Ubuntu 10.10, please refer to this [link]("http://ubuntuforums.org/showthread.php?t=1613000").
(2) Do you follow all the steps of the tutorial?
(3) Does your Touch Screen device is eGalax and the Device ID is the same as the tutorial?

Samiux

P.S. the program name for calibration is changed to "xinput_calibrator".

Hi.
Thanks for your replay.

1. I use Ubuntu 10.04 on a EEE PC 900
2. Yes I think that. I am a beginners to Ubuntu and I have follow this tutorial [http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html)

3. It looks like this:
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The calibrator info looks like this:
Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=10
    current calibration values (from XInput): min_x=1965, max_x=84 and min_y=201, max_y=1890

Doing dynamic recalibration:
    Setting new calibration data: 1965, 85, 196, 1885


--> Making the calibration permanent <--
  Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 1965 85 196 1885

Thanks for your help / P.S

---

### Post by samiux on 2011-01-18
> **Mr P.S said:**
> Hi.
Thanks for your replay.

1. I use Ubuntu 10.04 on a EEE PC 900
2. Yes I think that. I am a beginners to Ubuntu and I have follow this tutorial [http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html)

3. It looks like this:
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The calibrator info looks like this:
Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=10
    current calibration values (from XInput): min_x=1965, max_x=84 and min_y=201, max_y=1890

Doing dynamic recalibration:
    Setting new calibration data: 1965, 85, 196, 1885


--> Making the calibration permanent <--
  Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 1965 85 196 1885

Thanks for your help / P.S

Please complete Step 1 to 2 and list out the Step 3 here :

```
sudo nano /usr/lib/X11/xorg.conf.d/05-evdev.conf
```

Samiux

---

### Post by Mr P.S on 2011-01-18
> **samiux said:**
> Please complete Step 1 to 2 and list out the Step 3 here :

```
sudo nano /usr/lib/X11/xorg.conf.d/05-evdev.conf
```Samiux

Hi.
It looks like this:

        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

I have add this;

Section "InputClass"
   Identifier "eGalax"
   MatchProduct "eGalax"
   MatchDevicePath "/dev/input/event*"
   Driver "evdev"
   Option "SwapAxes" "off"
   Option "Calibration" "1965 85 209 1892"

Loock this ok?

I have follow the steps and the touchscreen is not responding.

---

### Post by samiux on 2011-01-18
> **Mr P.S said:**
> Hi.
It looks like this:

        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

I have add this;

Section "InputClass"
   Identifier "eGalax"
   MatchProduct "eGalax"
   MatchDevicePath "/dev/input/event*"
   Driver "evdev"
   Option "SwapAxes" "off"
   Option "Calibration" "1965 85 209 1892"

Loock this ok?

I have follow the steps and the touchscreen is not responding.

Make sure the "usbtouchscreen" is blacklisted :

**Step 1 :**

```
Boot up the system and press "Ctrl+Alt+F2" to go to command prompt.

sudo nano /etc/default/grub

Append "i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40" to "GRUB_CMDLINE_LINUX_DEFAULT".

*where i8042.noloop=1 solves the touchpad probem.

It will look like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"

Save and exit.

sudo update-grub
```

I think "i8042.noloop=1" is not required on your system.

**Step 2 :**

```
sudo nano /etc/modprobe.d/blacklist.conf

Append the following to the file.

blacklist usbtouchscreen
```

After that, you should reboot your box.

Samiux

---

### Post by Mr P.S on 2011-01-19
Hi.
I have follow the steps:
 
**Step 1 :**
 
[CODE]Boot up the system and press "Ctrl+Alt+F2" to go to command prompt.
 
sudo nano /etc/default/grub
 
And add: i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
 
GNU nano 2.2.2 Fil: /etc/default/grub 
 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"
GRUB_CMDLINE_LINUX=""
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
 
**It does not work with or ****without** i8042.noloop=1 or i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
 
 
 
 **Step 2 :**
 
sudo nano /etc/modprobe.d/blacklist.conf
 
Append the following to the file: blacklist usbtouchscreen
 
Looks like this:
 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
 
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
 
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
blacklist usbtouchscreen
 
# replaced by e100
blacklist eepro100
 
# replaced by tulip
blacklist de4x5
 
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
 
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
It still not working.
Do you have some more ideas?
Thanks for your patience / Peter

---

### Post by samiux on 2011-01-19
> **Mr P.S said:**
> Hi.
I have follow the steps:
 
**Step 1 :**
 
```
Boot up the system and press "Ctrl+Alt+F2" to go to command prompt.
 
sudo nano /etc/default/grub
 
And add: i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
 
GNU nano 2.2.2 Fil: /etc/default/grub 
 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"
GRUB_CMDLINE_LINUX=""
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
 
**It does not work with or ****without** i8042.noloop=1 or i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
 
 
 
 **Step 2 :**
 
sudo nano /etc/modprobe.d/blacklist.conf
 
Append the following to the file: blacklist usbtouchscreen
 
Looks like this:
 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
 
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
 
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
blacklist usbtouchscreen
 
# replaced by e100
blacklist eepro100
 
# replaced by tulip
blacklist de4x5
 
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
 
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
It still not working.
Do you have some more ideas?
Thanks for your patience / Peter

I think you missed the following command :

[CODE]sudo update-grub
```

Samiux

---

### Post by Mr P.S on 2011-01-19
> **samiux said:**
> I think you missed the following command :
 
```
sudo update-grub
```
 
Samiux
 
Hi.
I have updated grub and reboot and the touchscreen will not respond.
I restart the computer and try calibrate touchscreen.
Do I get error message: No calibratable devices found

Does it matter if I have device 004?
Bus 001 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
I think you have device 005
 
Peter

---

### Post by samiux on 2011-01-19
> **Mr P.S said:**
> Hi.
I have updated grub and reboot and the touchscreen will not respond.
I restart the computer and try calibrate touchscreen.
Do I get error message: No calibratable devices found

Does it matter if I have device 004?
Bus 001 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
I think you have device 005
 
Peter

Sorry, I have no idea about that.

Does your touch screen work on Windows?

Samiux

---

### Post by samiux on 2011-01-19
> **Mr P.S said:**
> Hi.
I have updated grub and reboot and the touchscreen will not respond.
I restart the computer and try calibrate touchscreen.
Do I get error message: No calibratable devices found

Does it matter if I have device 004?
Bus 001 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
I think you have device 005
 
Peter

Sorry, I have no idea about that.

Does your touch screen work on Windows?

Samiux

---

### Post by Mr P.S on 2011-01-19
> **samiux said:**
> Sorry, I have no idea about that.
 
Does your touch screen work on Windows?
 
Samiux
 
Hi
 
I do not know if it works with windows.

But if I remove the stage 1 and 2 
Calibrate the toushscreen
It will works it until I restart the computer.
 
Is it possible to keep Calibrated touchscreen after reboot.
Without steps 1 and 2?
 
Thanks a lot for your help / Peter

---

### Post by miegiel on 2011-01-19
> **Mr P.S said:**
> Hi
 
I do not know if it works with windows.

But if I remove the stage 1 and 2 
Calibrate the toushscreen
It will works it until I restart the computer.
 
Is it possible to keep Calibrated touchscreen after reboot.
Without steps 1 and 2?
 
Thanks a lot for your help / Peter

That is what step 3 does, the */usr/lib/X11/xorg.conf.d/05-evdev.conf* file gets read as X starts up. Maybe the howto should be more clear on that.

The line
```
Option "Calibration" "2 4100 11 4099"
```
sets the calibration. (Replace the calibration values with your own, mine are: 6 4088 0 4092)

---

### Post by Mr P.S on 2011-01-19
> **miegiel said:**
> That is what step 3 does, the */usr/lib/X11/xorg.conf.d/05-evdev.conf* file gets read as X starts up. Maybe the howto should be more clear on that.
 
The line
```
Option "Calibration" "2 4100 11 4099"
```
sets the calibration. (Replace the calibration values with your own, mine are: 6 4088 0 4092)
 
Hi.
I have add my own values:
Section "InputClass"
Identifier "eGalax"
MatchProduct "eGalax"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
Option "SwapAxes" "off"
Option "Calibration" "1965 85 209 1892"
 
If I follow the steps 1-3 and rebot.
I restart the computer and try calibrate touchscreen.
Do I get error message: No calibratable devices found
and the touchscreen will not respond
 
But if I remove the stage 1 and 2 
Calibrate the toushscreen
It will works it until I restart the computer.
After a restart I must do a new calibration
 
Peter

---

### Post by miegiel on 2011-01-19
> **Mr P.S said:**
> Hi.
I have add my own values:
Section "InputClass"
Identifier "eGalax"
MatchProduct "eGalax"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
Option "SwapAxes" "off"
Option "Calibration" "1965 85 209 1892"
 
If I follow the steps 1-3 and rebot.
I restart the computer and try calibrate touchscreen.
Do I get error message: No calibratable devices found
and the touchscreen will not respond
 
But if I remove the stage 1 and 2 
Calibrate the toushscreen
It will works it until I restart the computer.
After a restart I must do a new calibration
 
Peter

Doing Step 3 makes you load your touchscreen settings during boot. So that makes sense ;)

Do you really need to calibrate?

See if you can find what calibration values other EEE PC 900 owners use. If the calibration values you use work and are accurate your tablet is calibrated. Also, compiling a calibration tool might not be the best way for you to calibrate your screen. There are other ways. I just read the calibration values to use from the terminal with *evtest*.

X axis calibration
```
evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 53"
```
Y axis calibration
```
evtest /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 | grep "code 54"
```
You might need to change the path to the device and *| grep "code 53"* and *| grep "code 54"* might not work for you (try cutting it off or changing the numbers). **ps** use *Ctrl+C* to exit *evtest*.

---

### Post by Mr P.S on 2011-01-21
[QUOTE=miegiel;10377350]Doing Step 3 makes you load your touchscreen settings during boot. So that makes sense ;)
 
Do you really need to calibrate?
 
See if you can find what calibration values other EEE PC 900 owners use. If the calibration values you use work and are accurate your tablet is calibrated. Also, compiling a calibration tool might not be the best way for you to calibrate your screen. There are other ways. I just read the calibration values to use from the terminal with *evtest*.
 
Finally working my touchscreen. :D
I do not really know what was wrong.
But I did the following:
 
1 Added the command:
Edited / etc / modules, realize things
 
Code:
usbtouchscreen
usbhid
 
2 Clearing my hard drive.
Uninstalled XInput and something more.
and rebooted
 
3 Followed Samuax guide.
 
"lsusb" shows the following :
Bus 005 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Step 1 :
Boot up the system and press "Ctrl+Alt+F2" to go to command prompt.
sudo nano /etc/default/grub
Append "i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40" to "GRUB_CMDLINE_LINUX_DEFAULT".
*where i8042.noloop=1 solves the touchpad probem.
It will look like this :
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"
Save and exit.
sudo update-grub
Step 2 :
sudo nano /etc/modprobe.d/blacklist.conf
Append the following to the file.
blacklist usbtouchscreen
Step 3 :
sudo mkdir /usr/lib/X11/xorg.conf.d
sudo nano /usr/lib/X11/xorg.conf.d/05-evdev.conf
Append the following to the file.
Section "InputClass"
Identifier "eGalax"
MatchProduct "eGalax"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
Option "SwapAxes" "off"
Option "Calibration" "2 4100 11 4099"
EndSection
The value of calibration is "2 4100 11 4099" is perfect on my Gigabyte TouchNote T1028X (resolution 1366 x 768). However, you can change the value after doing Step 6 when necessary.
Step 4 :
The current version of xinput-calibrator is 0.7.5 at the time of this writing.
wget [[COLOR=#980101]https://github.com/downloads/tias/xinpu &#8230; 1_i386.deb[/COLOR]]("https://github.com/downloads/tias/xinput_calibrator/xinput-calibrator_0.7.5-1ubuntu1_i386.deb") --no-check-certificate
sudo dpkg -i xinput-calibrator_0.7.5-1ubuntu1_i386.deb
Step 5 :
Reboot your system.
Step 6 (Optional) :
To calibration your system and edit the value to Step 3 when necessary.
xinput_calibrator
Step 7 (Optional) :
Get uTouch (Multi-touch). However, this netbook does not support multi-touch. The following procedure does not causing harm to your system anyway.
sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update
sudo apt-get install utouch
Testing program.
sudo apt-get install python-pymt
python /usr/share/pymt-examples/launcher-multi.py
python /usr/share/pymt-examples/games/bubblebattles/bubblebatte.py
That's all! See you.
Posted by Samiux at 09:00
Labels: eGalax, Gigabyte T1028X, Ubuntu, uTouch
 
I had inverted axes x and y
There I solved this:
 
Option "SwapAxes" "1"
 
Section "InputClass"
 Identifier "calibration"
 MatchProduct "eGalax Inc. Touch"
 Option "Calibration" "1876 116 1719 101"
EndSection
 
Thanks for the help :D

---

### Post by michelepolo on 2011-02-27
> **Muzafsh said:**
> Thanks people, issue resolved

did the following...

Created the following file...
/etc/X11/xorg.conf.d/99-calibration.conf

and pasted the following set of snippets that threw up after calibration.

----------------------------------
Section "InputClass"
Identifier	"calibration"
MatchProduct	"eGalax Inc. Touch"
Option	"Calibration"	"1947 137 139 1755"
Option	"SwapAxes"	"1"
EndSection

Section "InputClass"
Identifier	"calibration"
MatchProduct	"eGalax Inc. Touch"
Option	"Calibration"	"139 1949 1750 134"
EndSection
----------------------------------

and Wallah !!! my calibration got set permanently

:)

thanks Samiux for your wiki, i managed to get my modded eeepc 701 touch screen! (ubuntu 10.04)

one thing seems different, i added your 99-calibration.conf but just the very first section, not the second
and also i excluded 10-evtouch.conf that i have on the same directory

my advice is to run xinput_calibration a couple of times, and tune the output

thanks!
michele

---

### Post by jgeissin on 2011-04-04
New hardware, same driver/problem:
ASUS PC (486), Ubuntu 10.04, patched to date, no-name 17" touchscreen monitor, POSX USB point of sale printer (USB), HP USB keyboard, Logitech USB mouse, Symbol USB barcode scanner.

Y axis is OK, poke your finger at the screen and the mouse goes there (center of the screen).  Up and down follows; side to side is reversed.

**uname -a:** Linux POPOS1 2.6.32-30-generic-pae #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 i686 GNU/Linux
**lsmod:**
Module                  Size  Used by
snd_hda_codec_analog    58598  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_intel          22133  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288290  3 
joydev                  8740  0 
drm_kms_helper         29329  1 i915
snd                    54180  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
drm                   163034  4 i915,drm_kms_helper
usblp                  10481  0 
usbhid                 36206  0 
asus_atk0110            9017  0 
usbtouchscreen          8073  0 
hid                    67096  1 usbhid
soundcore               6620  1 snd
lp                      7028  0 
serio_raw               3978  0 
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
r8169                  34364  0 
mii                     4381  1 r8169

**lsusb:**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05e0:1200 Symbol Technologies DS6608 Bar Code Scanner
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 002: ID 0525:a700 Netchip Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**05-evdev.conf:**
# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
   Identifier "eGalax"
   MatchProduct "EVTouch TouchScreen"
   MatchDevicePath "/dev/input/event*"
   Driver "evdev"
   Option "InvertX" "1"
   Option "Calibration" "1435 183 217 1138"
EndSection

**99-calibration.conf:**
Section "InputClass"
Identifier "calibration"
MatchProduct "eGalax Inc. Touch"
Option "Calibration" "1947 137 139 1755"
Option "InvertX" "1"
EndSection

Section "InputClass"
Identifier "calibration"
MatchProduct "eGalax Inc. Touch"
Option "Calibration" "1435 183 217 1138"
EndSection

PS.  What happened to xorg.conf????
Thanks!
Jon G

---

### Post by samiux on 2011-04-08
> **jgeissin said:**
> New hardware, same driver/problem:
ASUS PC (486), Ubuntu 10.04, patched to date, no-name 17" touchscreen monitor, POSX USB point of sale printer (USB), HP USB keyboard, Logitech USB mouse, Symbol USB barcode scanner.

Y axis is OK, poke your finger at the screen and the mouse goes there (center of the screen).  Up and down follows; side to side is reversed.

**uname -a:** Linux POPOS1 2.6.32-30-generic-pae #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 i686 GNU/Linux
**lsmod:**
Module                  Size  Used by
snd_hda_codec_analog    58598  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_intel          22133  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288290  3 
joydev                  8740  0 
drm_kms_helper         29329  1 i915
snd                    54180  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
drm                   163034  4 i915,drm_kms_helper
usblp                  10481  0 
usbhid                 36206  0 
asus_atk0110            9017  0 
usbtouchscreen          8073  0 
hid                    67096  1 usbhid
soundcore               6620  1 snd
lp                      7028  0 
serio_raw               3978  0 
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
r8169                  34364  0 
mii                     4381  1 r8169

**lsusb:**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05e0:1200 Symbol Technologies DS6608 Bar Code Scanner
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 002: ID 0525:a700 Netchip Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**05-evdev.conf:**
# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
   Identifier "eGalax"
   MatchProduct "EVTouch TouchScreen"
   MatchDevicePath "/dev/input/event*"
   Driver "evdev"
   Option "InvertX" "1"
   Option "Calibration" "1435 183 217 1138"
EndSection

**99-calibration.conf:**
Section "InputClass"
Identifier "calibration"
MatchProduct "eGalax Inc. Touch"
Option "Calibration" "1947 137 139 1755"
Option "InvertX" "1"
EndSection

Section "InputClass"
Identifier "calibration"
MatchProduct "eGalax Inc. Touch"
Option "Calibration" "1435 183 217 1138"
EndSection

PS.  What happened to xorg.conf????
Thanks!
Jon G

Try to add ```
Option "InvertY" "1"
```

---

### Post by lumix on 2011-05-24
Been trying desperately to get this to work on 11.04 with an Acer Iconia W500 (eGalax touchscreen) but no go.  Gestures are never recognized, and the touchscreen only behaves like a simple mouse.  It does work in Windows 7 with multitouch gestures.  I could really use some help with this.  No idea where to even begin troubleshooting, but I can provide any log or other output required.

---

### Post by allix81 on 2011-06-13
I have a Acer Iconia W500 as well, it would be great to have mutlti-touch, gestures and  autorotation working

---

### Post by bobmoser on 2011-07-17
lumix, did you ever get multitouch working on the Acer Iconia Tab W500, I just ordered one, and plan to remove windows 7 right away.

---

### Post by clauswilson on 2011-08-03
I have eGalax and followed samiux's guide ([http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html)).
Now the touchscreen is responding but it isn't behaving the way it should.
I tried to use xinput_calibrator_x11 and now when I move x-directions it goes the opposite. When I move y-directions it doesn't point right under my finger.
How do I correct this?
(Acer A150 - 8,9' screen)
(By the way how do I find my Ubuntu version? I often miss that)

---

### Post by clauswilson on 2011-08-03
Okay. That was simple. I just moved around with the numbers like this:
xinput set-prop --type int --format 32 "eGalax Inc. Touch" "Evdev Axis Calibration" 1938 57 162 1979 

(I purchased from VisualTouchWorld.com. They provide a driver which unfortunetely doesn't find my card.)

---

### Post by Muzafsh on 2011-10-15
**@clauswilson**

Can you please simplify the fix that worked for you!!! - as per your last post. 
A step-by-step help will greatly help me in fixing my touch screen with calibration that never worked since i upgraded to Natty. (My touch worked perfectly on Karmic - and it works perfectly on my other boot of Windows 7 even now...as i write)

thanks.

---

### Post by miegiel on 2011-10-16
> **Muzafsh said:**
> **@clauswilson**

Can you please simplify the fix that worked for you!!! - as per your last post. 
A step-by-step help will greatly help me in fixing my touch screen with calibration that never worked since i upgraded to Natty. (My touch worked perfectly on Karmic - and it works perfectly on my other boot of Windows 7 even now...as i write)

thanks.

Consider a clean install of oneiric (ubuntu 11.10) instead of upgrading (backup the important stuff in your home first though). The "input" parts of ubuntu have been changing in almost every release the past few years. And if you use exotic input devices (touchscreens etc.), the settings of the old ubuntu can mess up the updated ubuntu.

```
xinput set-prop --type int --format 32 "eGalax Inc. Touch" "Evdev Axis Calibration" 1938 57 162 1979
```
Sets the input properties (*"Evdev Axis Calibration"*) for the *"eGalax Inc. Touch"* device.

For more info on *xinput* see:
[http://manpages.ubuntu.com/manpages/oneiric/en/man1/xinput.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/xinput.1.html)

Note that changes you make using *xinput* don't persist after rebooting, so you will have to put it in a boot script (or login script).

---

### Post by raphaelsaldanha on 2011-10-17
Hi!

Had anyone tried this with 11.10 on a Dell Duo? I will try next week, and would like to know if it works...

How can I setup the 11.10 and maintain the 10.10 (I have not upgraded to 11.04).

---

### Post by miegiel on 2011-10-17
> **raphaelsaldanha said:**
> Hi!

Had anyone tried this with 11.10 on a Dell Duo? I will try next week, and would like to know if it works...

Yes, but I have the resistive version of the eGalax touch screen (ASUS T101MT, USB ID 0eef:480d). I believe your dell has the capacitive version.

Only problem so far is that, out of the box, only one finger clicking works. No right click menu or two finger scrolling. But I've only installed it for a few hours and haven't used it much. Still need to work on rotating the display and the touchscreen.

> How can I setup the 11.10 and maintain the 10.10 (I have not upgraded to 11.04).

You can make a dual boot, or triple boot, if your already dual boot with windows. It boils down to creating another partition for a separate linux (you can "reuse" the swap partition). I'm sure you can find info on how to do it in this forum or at [help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by raphaelsaldanha on 2011-10-17
Thank you! Shoul I follow this tutorial: [http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html) ?

---

### Post by michelepolo on 2012-10-01
[QUOTE=samiux;9745870]Did you complete the Step 1?  Your system is required to reboot after doing the Step 1.


[CODE]Step 1 :

sudo nano /etc/default/grub

Append "i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40" to "GRUB_CMDLINE_LINUX_DEFAULT".

*where i8042.noloop=1 solves the touchpad probem.

It will look like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"

Save and exit.

sudo update-grub

thanks Samiux!
working also on a Eepc 701 G with ubuntu 12.04 and 12.10
eGalax touchscreen ID 0eef:0001 D-WAV

---

