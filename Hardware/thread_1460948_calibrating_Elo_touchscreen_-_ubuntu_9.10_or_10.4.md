---
title: "calibrating Elo touchscreen - ubuntu 9.10 or 10.4"
date: 2010-04-23
forum: Hardware
---

### Post by ahoros on 2010-04-23
I am having tough time connecting my external Elotouch intelitouch monitor to Dell latitude D420 laptop.
(via USB)

That is kernel is properly detecting the device - however the coordinates are reversed.
e.g. up is down and right is left

I have found examples how to configure it via xorg.conf -- however I belive that under recent version of x.org  that file is not used anymore.

Moreover the utility for calibration does not work:
root@wali:/etc/X11# ts_calibrate 
ts_open: No such file or directory


I tried both 9.10 and now I am struggling with 10.4 --- with no success.

I would appreciate any pointers  - anything that I was able to google on the web seems to be outdated.

Thanks


----------------------------------------------------------------

Apr 23 20:58:30 wali kernel: [ 2270.329073] usb 4-1: new full speed USB device using uhci_hcd and address 2
Apr 23 20:58:30 wali kernel: [ 2270.539306] usb 4-1: configuration #1 chosen from 1 choice
Apr 23 20:58:30 wali kernel: [ 2270.542169] hub 4-1:1.0: USB hub found
Apr 23 20:58:30 wali kernel: [ 2270.546002] hub 4-1:1.0: 4 ports detected
Apr 23 20:58:30 wali kernel: [ 2270.834111] usb 4-1.1: new low speed USB device using uhci_hcd and address 3
Apr 23 20:58:30 wali kernel: [ 2270.982346] usb 4-1.1: configuration #1 chosen from 1 choice
Apr 23 20:58:30 wali kernel: [ 2271.000637] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input15
Apr 23 20:58:30 wali kernel: [ 2271.000926] generic-usb 0003:045E:00E3.0004: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:1d.2-1.1/input0
Apr 23 20:58:30 wali kernel: [ 2271.142513] input: Microsft Microsoft Wireless Optical Desktop® 2.20 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input16
Apr 23 20:58:30 wali kernel: [ 2271.142790] generic-usb 0003:045E:00E3.0005: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop® 2.20] on usb-0000:00:1d.2-1.1/input1
Apr 23 20:58:31 wali kernel: [ 2271.217144] usb 4-1.3: new full speed USB device using uhci_hcd and address 4
Apr 23 20:58:31 wali kernel: [ 2271.378383] usb 4-1.3: configuration #1 chosen from 1 choice
Apr 23 20:58:31 wali kernel: [ 2271.412319] input: Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.3/4-1.3:1.0/input/input17
Apr 23 20:58:31 wali kernel: [ 2271.412615] generic-usb 0003:04E7:0007.0006: input,hidraw2: USB HID v1.00 Pointer [Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U] on usb-0000:00:1d.2-1.3/input0
root@wali:/etc/X11#

---

### Post by ahoros on 2010-04-25
I guess the question is should I try to install additional drivers for xorg
and try to configure it via xconf.org -- as most sites suggest (albeit for older version of kernel / xorg)

or is there any way to pass arguments to kernel
since it seems to be doing OK job of detecting the elo touch screen:

some people suggested passing arguments to HAL (for instance: [FONT=Verdana][SIZE=2] "wacom.fdi" in /etc/hal/fdi/policy[/SIZE][/FONT]) --- but no HAL anymore in 10.04  ...... and anyway I have Elo.



root@wali:/home/# xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                             id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9116;   &#8627; Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U    id=16    [slave  pointer  (2)]
&#9116;   &#8627; Microsft Microsoft Wireless Optical Desktop® 2.20    id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; Microsft Microsoft Wireless Optical Desktop® 2.20    id=15    [slave  keyboard (3)]
root@wali:/home/#



----------------------------



root@wali:/home/j# /usr/lib/xf86-input-evtouch/calibrate.sh
Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready.

root@wali:/home/# lshal 
Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready.
root@wali:/home/#

---

### Post by ahoros on 2010-04-25
Hurray! 

I found a solution in the following thread:
[http://ubuntuforums.org/showthread.php?t=1016744&highlight=elotouch](http://ubuntuforums.org/showthread.php?t=1016744&highlight=elotouch)

(also adjusted TAGS to link it better)


And here is the summary of what has worked for me - re: the **ELO touchscreen is reversed/backwards problem:**


a@wali:~$ cat /proc/bus/input/devices 
(...)

I: Bus=0003 Vendor=045e Product=00e3 Version=0111
N: Name="Microsft Microsoft Wireless Optical Desktop® 2.20"
P: Phys=usb-0000:00:1d.2-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input12
U: Uniq=
H: Handlers=kbd event12 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=107

I: Bus=0003 Vendor=045e Product=00e3 Version=0111
N: Name="Microsft Microsoft Wireless Optical Desktop® 2.20"
P: Phys=usb-0000:00:1d.2-1.1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input13
U: Uniq=
H: Handlers=kbd mouse3 event13 js0 
B: EV=10001f
B: KEY=837fff 2c3027 bf004444 0 c000000 1f0001 10f84 8a27c007 ffff7bfa d941dfff febeffdf ffefffff ffffffff fffffffe
B: REL=fc3
B: ABS=ffffff01 701ff
B: MSC=10

I: Bus=0003 Vendor=04e7 Product=0007 Version=0100
N: Name="Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U"
P: Phys=usb-0000:00:1d.2-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.3/4-1.3:1.0/input/input14
U: Uniq=07I11787
H: Handlers=mouse4 event14 js1 
B: EV=1b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3
B: MSC=10


a@wali:~$ xinput list-props "Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U"
Device 'Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U':
    Device Enabled (114):    1
    Device Accel Profile (233):    0
    Device Accel Constant Deceleration (234):    1.000000
    Device Accel Adaptive Deceleration (236):    1.000000
    Device Accel Velocity Scaling (237):    10.000000
    Evdev Reopen Attempts (231):    10
    Evdev Axis Inversion (238):    0, 0
    Evdev Axis Calibration (239):    <no items>
    Evdev Axes Swap (240):    0
    Axis Labels (241):    "Abs X" (501), "Abs Y" (502), "None" (0)
    Button Labels (242):    "Button Left" (115), "Button Unknown" (232), "Button Unknown" (232), "Button Wheel Up" (118), "Button Wheel Down" (119)
    Evdev Middle Button Emulation (243):    2
    Evdev Middle Button Timeout (244):    50
    Evdev Wheel Emulation (245):    0
    Evdev Wheel Emulation Axes (246):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (247):    10
    Evdev Wheel Emulation Timeout (248):    200
    Evdev Wheel Emulation Button (249):    4
    Evdev Drag Lock Buttons (250):    0


====> AND THE SOLUTION IS:
a@wali:~$ xinput set-int-prop "Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U"  "Evdev Axis Inversion" 8 1 1 



After issuing this command the properties look now like this:
a@wali:~$ xinput list-props "Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U"
Device 'Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U':
    Device Enabled (114):    1
    Device Accel Profile (233):    0
    Device Accel Constant Deceleration (234):    1.000000
    Device Accel Adaptive Deceleration (236):    1.000000
    Device Accel Velocity Scaling (237):    10.000000
    Evdev Reopen Attempts (231):    10
    Evdev Axis Inversion (238):    1, 1
    Evdev Axis Calibration (239):    <no items>
    Evdev Axes Swap (240):    0
    Axis Labels (241):    "Abs X" (501), "Abs Y" (502), "None" (0)
    Button Labels (242):    "Button Left" (115), "Button Unknown" (232), "Button Unknown" (232), "Button Wheel Up" (118), "Button Wheel Down" (119)
    Evdev Middle Button Emulation (243):    2
    Evdev Middle Button Timeout (244):    50
    Evdev Wheel Emulation (245):    0
    Evdev Wheel Emulation Axes (246):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (247):    10
    Evdev Wheel Emulation Timeout (248):    200
    Evdev Wheel Emulation Button (249):    4
    Evdev Drag Lock Buttons (250):    0

---

### Post by ahoros on 2010-04-27
Still need help! --> how to calibrate touchscreen

direction reversal problem is solved - but the screen still needs calibration - on the right hand side of the screen the mouse movement to actual touch area is off by about 1 centimeter!

The tslib calibration library seems to be still broken despite 10.4 final status )-:

---

### Post by Interruptor on 2010-05-06
I've made this [quick and ugly] script to calibrate "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U"
```
device_id=$(zenity --entry --text="`xinput list`\n_________\n\ndevice id:")
minx=1000
maxx=3655
miny=960
maxy=3314
errors_status=""
while `zenity --question --text="$errors_status\n___\n\n$minx,$maxx,$miny,$maxy\nAgain?"`; do 
	minx=`zenity --scale --text="min-x" --value=$minx --min-value=500 --max-value=1100 --step=5`
	maxx=`zenity --scale --text="max-x" --value=$maxx --min-value=3200 --max-value=4000 --step=5`
	miny=`zenity --scale --text="min-y" --value=$miny --min-value=800 --max-value=1100 --step=5`
	maxy=`zenity --scale --text="max-y" --value=$maxy --min-value=3000 --max-value=3600 --step=5`
	errors_status="`xinput --set-prop "$device_id" "Evdev Axis Calibration" $minx, $maxx, $miny, $maxy 2>&1`"
done
```
For sitting: 1000,3655,970,3325
For standing: 1000,3655,960,3314

---

### Post by Noob Programmer on 2010-05-11
Thanks so much for that calibration script. I had to change the min and max values past what you were allowing.
min-x 50
max-x 3990
min-y 50
max-y 4080

---

### Post by Interruptor on 2010-05-17
Detection of device id:
```
device_id=`xinput list | grep Touch | grep -o "id=[0-9]*" | sed 's/id=//'`
```

---

### Post by Interruptor on 2010-06-05
Just found [http://sourceforge.net/projects/evcalibrate/](http://sourceforge.net/projects/evcalibrate/)
Can someone test it and post returned values here?
Because I will be able to test it myself only in 2+ days.

If it's working, then we can mark thread as solved.

---

### Post by Favux on 2010-06-05
Hi,

On this [elo thread]("http://ubuntuforums.org/showthread.php?t=1483778&page=3") dglnz used [touchcal]("http://touchcal.sourceforge.net/") to calibrate.

---

### Post by Interruptor on 2010-06-15
Yeap, **evcalibrate** working perfectly.

```
$ sudo ./evcalibrate /dev/input/by-id/usb-Elo_TouchSystems_Inc._Elo_TouchSystems_IntelliTouch_2500U_07U01964-event-mouse
xinput set-int-prop "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U" "Evdev Axis Calibration" 32 990 3686 936 3341
xinput set-int-prop "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U" "Evdev Axis Inversion" 8 0 1
xinput set-int-prop "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U" "Evdev Axes Swap" 8 0
```
So, **990 3686 936 3341** for 17" IntelliTouch 2500U

Just had to *make* and run it under root and installed next packages before compiling:
> libqt4-opengl-dev
qt4-qmake

I think this should be added to first post and thread marked as solved.

Favux, thanks, but touchcal is not my case:
> Supported Hardware
------------------
 - EloGraphics(R) IntelliTouch E281-2310 (serial)
 - MicroTouch(R) SMT3 (serial)

**No USB** touchscreens are supported at this time, but patches to support
different configurations and new hardware are very welcome.

---

### Post by jreiner3 on 2010-06-29
Firstly this has been the most useful thread for solving my Elo touchscreen calibration issues, kudos. 

I am trying to calibrate an Elo TouchSystems 2216 AccuTouch USB Touchmonitor Interface, and I cant use any of the aforementioned calibration tools. I am building this for an embedded system I do not have OpenGL, (there goes evcalibrate), its a USB touchscreen (c-ya touchcal) and Gawd help me if I can get the framebuffer to play nice so ts_lib is not working either. However thanks to you folks I have been able to solve the inverted axis issue, and through trial and error I am closing in on the min and max for X and Y. 

The issue that I still have is the one that ahoros mentioned in an earlier post. 

> Still need help! --> how to calibrate touchscreen

direction reversal problem is solved - but the screen still needs calibration - on the right hand side of the screen the mouse movement to actual touch area is off by about 1 centimeter!

I am actually a bit farther off the mark than ahoros, the cursor is approx 2 inches off from where I am touching the screen. I've looked at the available options under xinput ```
# xinput --help
usage :
	xinput get-feedbacks <device name>
	xinput set-ptr-feedback <device name> <threshold> <num> <denom>
	xinput set-integer-feedback <device name> <feedback id> <value>
	xinput get-button-map <device name>
	xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
	xinput set-pointer <device name> [<x index> <y index>]
	xinput set-mode <device name> ABSOLUTE|RELATIVE
	xinput list [--loop || --short || <device name>...]
	xinput query-state <device name>
	xinput test [-proximity] <device name>
	xinput version 
	xinput list-props <device> [<device> ...]
	xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
	xinput set-float-prop <device> <property> <val> [<val> ...]
	xinput set-atom-prop <device> <property> <val> [<val> ...]
	xinput watch-props <device>
	xinput delete-prop <device> <property>

```

Not sure which of these options I need to use. set-ptr-feedback looks the most promising but what values to use? Any help is greatly appreciated thanks.

---

### Post by kqr2 on 2010-06-30
This thread has been very informative. I was able to fix the axes / swap issues and calibrate using evcalibrate.

Another question:  does anyone know how to enable a beeping sound on touch / click events?

It looks like the elo driver has the beep capability, however, I would like to stick with evdev since it's working now.

[http://www.elotouch.com/files/install/elo_linux_serial_driver_v3.2_installation_instructions.txt](http://www.elotouch.com/files/install/elo_linux_serial_driver_v3.2_installation_instructions.txt)

---

### Post by kqr2 on 2010-06-30
> **jreiner3 said:**
> Firstly this has been the most useful thread for solving my Elo touchscreen calibration issues, kudos. 

I am trying to calibrate an Elo TouchSystems 2216 AccuTouch USB Touchmonitor Interface, and I cant use any of the aforementioned calibration tools. I am building this for an embedded system I do not have OpenGL, (there goes evcalibrate), its a USB touchscreen (c-ya touchcal) and Gawd help me if I can get the framebuffer to play nice so ts_lib is not working either. However thanks to you folks I have been able to solve the inverted axis issue, and through trial and error I am closing in on the min and max for X and Y. 

The issue that I still have is the one that ahoros mentioned in an earlier post. 



I am actually a bit farther off the mark than ahoros, the cursor is approx 2 inches off from where I am touching the screen. I've looked at the available options under xinput ```
# xinput --help
usage :
    xinput get-feedbacks <device name>
    xinput set-ptr-feedback <device name> <threshold> <num> <denom>
    xinput set-integer-feedback <device name> <feedback id> <value>
    xinput get-button-map <device name>
    xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
    xinput set-pointer <device name> [<x index> <y index>]
    xinput set-mode <device name> ABSOLUTE|RELATIVE
    xinput list [--loop || --short || <device name>...]
    xinput query-state <device name>
    xinput test [-proximity] <device name>
    xinput version 
    xinput list-props <device> [<device> ...]
    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
    xinput set-float-prop <device> <property> <val> [<val> ...]
    xinput set-atom-prop <device> <property> <val> [<val> ...]
    xinput watch-props <device>
    xinput delete-prop <device> <property>

```Not sure which of these options I need to use. set-ptr-feedback looks the most promising but what values to use? Any help is greatly appreciated thanks.

As mentioned in an earlier thread, you can set the x-min, x-max, y-min, y-max values using:

xinput set-int-prop "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U" "Evdev Axis Calibration" 32 990 3686 936 3341

---

### Post by lymchan on 2010-07-05
I'm a bit of a newbie to compiling on Ubuntu, trying to get my touchscreen working on an old eeePC, can you help me out?

Here's what I have done so far:

```
sudo apt-get install qt4-qmake
sudo apt-get install libqt4-opengl-dev
```

I have downloaded evcalibrate, and identified my PATH-TO-NODE-EVENT and the code I would use(once in my extracted evcalibrate directory) would thus be:

```
$ sudo ./evcalibrate /dev/input/by-id/usb-eGalax_Inc._Touch-event-mouse
```

The place I am lost with is what you said here:

> **Interruptor said:**
> 
Just had to *make* and run it under root 


Can you (or anyone) tell me line by line by that actually means and how I do that?

Thanks in advance...

---

### Post by kqr2 on 2010-07-06
> **lymchan said:**
> I'm a bit of a newbie to compiling on Ubuntu, trying to get my touchscreen working on an old eeePC, can you help me out?

Here's what I have done so far:

```
sudo apt-get install qt4-qmake
sudo apt-get install libqt4-opengl-dev
```I have downloaded evcalibrate, and identified my PATH-TO-NODE-EVENT and the code I would use(once in my extracted evcalibrate directory) would thus be:

```
$ sudo ./evcalibrate /dev/input/by-id/usb-eGalax_Inc._Touch-event-mouse
```The place I am lost with is what you said here:



Can you (or anyone) tell me line by line by that actually means and how I do that?

Thanks in advance...

Have you successfully compiled evcalibrate?

If not:

* extract evcalibrate:

tar xvzf evcalibrate-0.5.1-r1.tgz

* in evcalibrate directory:

qmake
make

* you should then be able to run evcalibrate

---

### Post by lymchan on 2010-07-07
Hi, thanks for the reply.

Here's what I get:

```
poonet@poonet-laptop:~$ cd EVcalibrate
poonet@poonet-laptop:~/EVcalibrate$ qmake
poonet@poonet-laptop:~/EVcalibrate$ make
g++ -c -pipe -O2 -g -Wall -W -D_REENTRANT -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I. -I/usr/include -I/usr/X11R6/include -I. -o main.o main.cpp
make: g++: Command not found
make: *** [main.o] Error 127
```

Am I doing something wrong? Any recommendations?

---

### Post by kqr2 on 2010-07-09
> **lymchan said:**
> Hi, thanks for the reply.

Here's what I get:

```
poonet@poonet-laptop:~$ cd EVcalibrate
poonet@poonet-laptop:~/EVcalibrate$ qmake
poonet@poonet-laptop:~/EVcalibrate$ make
g++ -c -pipe -O2 -g -Wall -W -D_REENTRANT -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I. -I/usr/include -I/usr/X11R6/include -I. -o main.o main.cpp
make: g++: Command not found
make: *** [main.o] Error 127
```Am I doing something wrong? Any recommendations?

It looks like you don't have gcc installed.  Make sure  you have build-essential installed.

sudo apt-get install build-essential

Then try make again.

---

### Post by lymchan on 2010-07-10
Great, I did that and it seems to have installed correctly, and entering qmake then make seemed to successfully compile as well.  I feel like I am so close.. but still no cigar as yet:

```
root@poonet-laptop:/home/poonet# cd EVcalibrate
root@poonet-laptop:/home/poonet/EVcalibrate# dir
configWriter.cpp  main.cpp	   mathUtility.o	 moc_systemWorkspace.cpp
configWriter.h	  main.h	   moc_configWriter.cpp  moc_systemWorkspace.o
configWriter.o	  main.o	   moc_configWriter.o	 README
evcalibrate	  mainWindow.cpp   moc_eventMonitor.cpp  systemView.cpp
evcalibrate.pro   mainWindow.h	   moc_eventMonitor.o	 systemView.h
eventMonitor.cpp  mainWindow.o	   moc_mainWindow.cpp	 systemView.o
eventMonitor.h	  Makefile	   moc_mainWindow.o	 systemWorkspace.cpp
eventMonitor.o	  mathUtility.cpp  moc_systemView.cpp	 systemWorkspace.h
INSTALL		  mathUtility.h    moc_systemView.o	 systemWorkspace.o
root@poonet-laptop:/home/poonet/EVcalibrate# $ sudo ./evcalibrate /dev/input/by-id/usb-eGalax_Inc._Touch-event-mouse
$: command not found
root@poonet-laptop:/home/poonet/EVcalibrate# evcalibrate
evcalibrate: command not found
```

As you can see from the dir, the evcalibrate file does now exist, and yet the terminal says that it can't find the command :S.  WT?

---

### Post by kqr2 on 2010-07-12
> **lymchan said:**
> Great, I did that and it seems to have installed correctly, and entering qmake then make seemed to successfully compile as well.  I feel like I am so close.. but still no cigar as yet:

```
root@poonet-laptop:/home/poonet# cd EVcalibrate
root@poonet-laptop:/home/poonet/EVcalibrate# dir
configWriter.cpp  main.cpp       mathUtility.o     moc_systemWorkspace.cpp
configWriter.h      main.h       moc_configWriter.cpp  moc_systemWorkspace.o
configWriter.o      main.o       moc_configWriter.o     README
evcalibrate      mainWindow.cpp   moc_eventMonitor.cpp  systemView.cpp
evcalibrate.pro   mainWindow.h       moc_eventMonitor.o     systemView.h
eventMonitor.cpp  mainWindow.o       moc_mainWindow.cpp     systemView.o
eventMonitor.h      Makefile       moc_mainWindow.o     systemWorkspace.cpp
eventMonitor.o      mathUtility.cpp  moc_systemView.cpp     systemWorkspace.h
INSTALL          mathUtility.h    moc_systemView.o     systemWorkspace.o
root@poonet-laptop:/home/poonet/EVcalibrate# $ sudo ./evcalibrate /dev/input/by-id/usb-eGalax_Inc._Touch-event-mouse
$: command not found
root@poonet-laptop:/home/poonet/EVcalibrate# evcalibrate
evcalibrate: command not found
```As you can see from the dir, the evcalibrate file does now exist, and yet the terminal says that it can't find the command :S.  WT?

You had a copy and paste typo.  You typed "$ sudo ./evcalibrate" ... no $; just:

sudo ./evcalibrate ...

If you are already root, e.g. # prompt, you can just do:

./evcalibrate ...

---

### Post by lymchan on 2010-07-14
One step forward, two steps back...

So you were right, getting rid of the typo did get evcalibrate to activate, and I get a "preparing touchscreen for calibration..." screen showing.  Unfortunately that's all I get, it just hangs there.  

So I thought, maybe I should check that my touchscreen is still detected.  It used to be (ever since Lucid NBR install) that when I hit anywhere on the screen the cursor moved/clicked to the upper left corner.  After running evcalibrate, it does so no longer.  Also, when I check dev/input, there is no longer a "by-id" folder, let alone my usb-eGalax-etc event file.

I am persevering with this dammit!  If there are no other recommendations, I'll try to reload Lucid NBR (or just boot via CD) to see if that brings back the touchscreen detection.

Thanks again.

---

### Post by jreiner3 on 2010-07-14
> **kqr2 said:**
> As mentioned in an earlier thread, you can set the x-min, x-max, y-min, y-max values using:

xinput set-int-prop "Elo TouchSystems Inc. Elo TouchSystems IntelliTouch 2500U" "Evdev Axis Calibration" 32 990 3686 936 3341

kqr2 saw that and tried it but it does not address my specific issue because I am not using the same monitor as the earlier poster. I have experimented with various numbers for min and max but there does not seem to be a linear relationship (i.e. more negative does not result in farther left) 

I am also hoping that once I get the min and max right the pointer will correspond to where I am actually touching the screen and not roughly 2 inches off.

---

### Post by kqr2 on 2010-07-14
> **lymchan said:**
> One step forward, two steps back...

So you were right, getting rid of the typo did get evcalibrate to activate, and I get a "preparing touchscreen for calibration..." screen showing.  Unfortunately that's all I get, it just hangs there.  

So I thought, maybe I should check that my touchscreen is still detected.  It used to be (ever since Lucid NBR install) that when I hit anywhere on the screen the cursor moved/clicked to the upper left corner.  After running evcalibrate, it does so no longer.  Also, when I check dev/input, there is no longer a "by-id" folder, let alone my usb-eGalax-etc event file.

I am persevering with this dammit!  If there are no other recommendations, I'll try to reload Lucid NBR (or just boot via CD) to see if that brings back the touchscreen detection.

Thanks again.

Check out this thread:

**[B]eGalax touchscreen setup and calibration in Ubuntu Lucid (with calibration tool)  **[/B]

[http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877)

---

### Post by lymchan on 2010-07-15
O, sweet, that looks exactly like what I need.  Thanks so much, this whole "get help from complete strangers from indeterminate location" thing is still pretty new to me, I hope to be able to return the favour somehow :).

---

### Post by jreiner3 on 2010-07-16
I know I'm kind of on my own out here but I figured out what worked for me and thought I'd post it just in case anyone ever found themselves in the same situation.

I ended up using a trial and error approach to finding the proper calibration parameters. When initially turned on the X axis was inverted so I had run the xinput set-int-prop etc to correct the inversion and had been trying to calibrate from there. It turned out that in order to get the screen calibrated I needed to undo the axis correction on X and invert Y!!! Which seems a bit weird but it worked for me. I then created this script to run at startup to calibrate the screen

```
#!/bin/bash

# This script is used to calibrate the touchscreen at startup

`sudo xinput set-int-prop 5 228  8 0 1`
`sudo xinput set-int-prop 5 229  32 2750 1050 2850 1050`

```

sudo was needed because the kiosk does not run under root. 

Also if you do 
```
xinput -list
```

it lists all the devices, my touchscreen was device 5, much easier than typing the complete name of the device!

Thanks again for the help

---

### Post by Interruptor on 2010-08-10
> **jreiner3 said:**
> 
```
#!/bin/bash

# This script is used to calibrate the touchscreen at startup

`sudo xinput set-int-prop [COLOR="Red"]**5**[/COLOR] 228  8 0 1`
`sudo xinput set-int-prop [COLOR="Red"]**5**[/COLOR] 229  32 2750 1050 2850 1050`

```

Be careful, device id can change if you connect or disconnect any input devices. I had this problem and solved it by this script:
[http://ubuntuforums.org/showpost.php?p=9313898&postcount=7](http://ubuntuforums.org/showpost.php?p=9313898&postcount=7)
```
device_id=`xinput list | grep Touch | grep -o "id=[0-9]*" | sed 's/id=//'`
```

---

### Post by konfuzius85 on 2010-09-05
Hey guys,
it seems as you are a step further with your ELO problems than I am.
I am trying to get my ELO 1715L Touchscreen working on a ubuntu 10.04-machine. The Display itself works, of course, but none of the touchscreen-function.
Which drivers are you using? The official ELO drivers are for older kernel versions only, and I couldn't find any working installation guide.
Thanks for any help and advices...

---

### Post by jreiner3 on 2010-09-16
> **Interruptor said:**
> Be careful, device id can change if you connect or disconnect any input devices. I had this problem and solved it by this script:
[http://ubuntuforums.org/showpost.php?p=9313898&postcount=7](http://ubuntuforums.org/showpost.php?p=9313898&postcount=7)
```
device_id=`xinput list | grep Touch | grep -o "id=[0-9]*" | sed 's/id=//'`
```

Yup you were exactly right, moved the flash to another machine and the id changed. Duh, sometimes I out smart myself! Thanks for the script.

---

### Post by etrnl on 2010-09-17
> **jreiner3 said:**
> kqr2 saw that and tried it but it does not address my specific issue because I am not using the same monitor as the earlier poster. I have experimented with various numbers for min and max but there does not seem to be a linear relationship (i.e. more negative does not result in farther left) 

I am also hoping that once I get the min and max right the pointer will correspond to where I am actually touching the screen and not roughly 2 inches off.

I am stuck in the same situation. The numbers don't seem consistent with the actual alignment. I almost got there but at the same time, when I touch other parts of the screen, it seems way off again. Any suggestions?

---

### Post by fritserasmus on 2011-08-12
Interruptor,
Quote from your notes:
"
So, 990 3686 936 3341 for 17" IntelliTouch 2500U

Just had to make and run it under root and installed next packages before compiling:
Quote:
libqt4-opengl-dev
qt4-qmake
I think this should be added to first post and thread marked as solved.
"
Could you perhaps help me by explaing how to:
"Make" it. I have noticed in the document:
[http://touchcal.sourceforge.net/](http://touchcal.sourceforge.net/)
it tells me to make it but after untar the files into one folder, I do not know what to do to start the calibrater:

I have: Ubuntu 11.04 and a 1939L Elo screen

Your help/assistence/pointers would be appreciated very much.

---

