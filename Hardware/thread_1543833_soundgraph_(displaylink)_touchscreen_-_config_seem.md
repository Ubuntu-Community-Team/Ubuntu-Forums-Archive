---
title: "soundgraph (displaylink) touchscreen - config seems ok but touch still not working"
date: 2010-08-01
forum: Hardware
---

### Post by xapient on 2010-08-01
i recently bought the soundgraph fingervu 706 touchscreen - this is a displaylink device :

[IMG]http://shop.soundgraph.com/Images/ProductImages/FingerVU_706/03.jpg[/IMG]

```
I: Bus=0003 Vendor=15c2 Product=3480 Version=0111
N: Name="SoundGraph,Inc.--- SoundGraph.Inc"
P: Phys=usb-0000:00:04.1-3.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3.2/1-3.2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=15c2 Product=3480 Version=0111
N: Name="SoundGraph,Inc.--- SoundGraph.Inc"
P: Phys=usb-0000:00:04.1-3.2/input1
S: Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3.2/1-3.2:1.1/input/input6
U: Uniq=
H: Handlers=sysrq kbd event6 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

```with the new 2.6.35 kernel (first i tried the one from the ppa and now im testing "maveric") the display is working fine.. (with 2.6.32 i see a white screen) everything i needed to do was install the xserver-xorg-video-displaylink package and write a simple xorg.conf

even the remote control does something out of the box :-)

now the problem: the touchscreen isn't working ! (i'm talking about the touch-INPUT-feature)

i already installed the xserver-xorg-input-evtouch package and Xorg.0.log says it is configured as mouse.  but nothing happens when i touch the screen.

i tried serveral configurations and wrote my own section in the xorg.conf 
(like this one: [http://www.pur3.co.uk/view.php?DisplayLink](http://www.pur3.co.uk/view.php?DisplayLink) )
i read everything i could find but still - no touch input - it makes no sense to me as everything seems to be oke - at least in the config/logs

with evdev driver Xorg.0.log says:
```

[   320.619] (**) Option "SendCoreEvents"
[   320.619] (**) touchscreen: always reports core events
[   320.619] (**) touchscreen: Device: "/dev/input/event5"
[   320.648] (II) touchscreen: Found 3 mouse buttons
[   320.648] (II) touchscreen: Found scroll wheel(s)
[   320.648] (II) touchscreen: Found relative axes
[   320.648] (II) touchscreen: Found x and y relative axes
[   320.648] (II) touchscreen: Configuring as mouse
[   320.648] (**) Option "Emulate3Buttons" "true"
[   320.648] (II) touchscreen: Forcing middle mouse button emulation on.
[   320.648] (**) Option "Emulate3Timeout" "50"
[   320.648] (**) touchscreen: YAxisMapping: buttons 4 and 5
[   320.648] (**) touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   320.648] (II) XINPUT: Adding extended input device "touchscreen" (type: MOUSE)
[   320.648] (II) touchscreen: initialized for relative axes.

```
with evtouch:
```

[   669.729] State: S_UNTOUCHED Action: No Action               Button: 0
[   669.730] State: S_TOUCHED   Action: No Action               Button: 0
[   669.730] State: S_LONGTOUCHED       Action: down            Button: 1
[   669.730] State: S_MOVING    Action: No Action               Button: 0
[   669.730] State: S_MAYBETAPPED       Action: click           Button: 1
[   669.730] State: S_ONEANDAHALFTAP    Action: down            Button: 3
[   669.730] (**) Option "MinX" "200"
[   669.730] (**) Option "MaxX" "4000"
[   669.730] (**) Option "MinY" "400"
[   669.730] (**) Option "MaxY" "4000"
[   669.730] (**) Option "Emulate3Buttons" "true"
[   669.730] (**) Option "Emulate3Timeout" "50"
[   669.730] (**) Option "TapTimer" "200"
[   669.731] (**) Option "MoveLimit" "0"
[   669.731] (**) Option "SendCoreEvents"
[   669.731] (**) EVTouch TouchScreen: always reports core events
[   669.731] (II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)
[   669.731] (**) Option "Device" "/dev/input/event5"
[   669.760] (II) EVTouch TouchScreen: Found 274 mouse buttons
[   669.760] (II) EVTouch TouchScreen: Found relative axes


```



please help! i can provide any further information if you need it....

thx in advance

---

### Post by xapient on 2010-08-03
i recently found out that i used the wrong device...  

> FingerVU is an USB composite device. This composite device consists of  HID keyboard device, HID mouse device and HID compliant device. HID  keyboard/mouse driver are used for IR input from remote control. The  touch data is transferred through HID compliant device driver.ls -l /dev/input/by-id/
 ```

usb-SoundGraph_Inc.---_SoundGraph.Inc-event-kbd -> ../event8
usb-SoundGraph_Inc.---_SoundGraph.Inc-event-mouse -> ../event7
usb-SoundGraph_Inc.---_SoundGraph.Inc-mouse -> ../mouse2 

```so i used /dev/input/mouse2  instead of eventX... now i get an error in /var/log/Xorg.0.log:

```

State: S_UNTOUCHED      Action: No Action               Button: 0
State: S_TOUCHED        Action: No Action               Button: 0
State: S_LONGTOUCHED    Action: down            Button: 1
State: S_MOVING Action: No Action               Button: 0
State: S_MAYBETAPPED    Action: click           Button: 1
State: S_ONEANDAHALFTAP Action: down            Button: 3
(**) Option "MinX" "200"
(**) Option "MaxX" "4000"
(**) Option "MinY" "400"
(**) Option "MaxY" "4000"
(**) Option "Emulate3Buttons" "true"
(**) Option "Emulate3Timeout" "50"
(**) Option "TapTimer" "200"
(**) Option "MoveLimit" "0"
(**) Option "SendCoreEvents"
(**) EVTouch TouchScreen: always reports core events
(II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)
(**) Option "Device" "/dev/input/mouse2"
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
Unable to query/initialize EVTouch hardware.
[dix] couldn't enable device 6
(EE) Couldn't init device "touchscreen"
(II) UnloadModule: "evtouch"

```
any ideas how to continue? :(

---

### Post by macrules on 2010-08-28
hi,

I fixed a similar error by putting extra config options in /usr/lib/X11/xorg.conf.d/10-evtouch
I removed it by now, but if you google you might find some usefull info.
I still do not have my GeneralTouch 0dfc:0001 working :(.
Hope this helps!

kind regards,
Vincent

---

### Post by macrules on 2010-08-28
Found it, by simply googling your error again:
[http://www.viitalat.net/index.php/htpc/2010/07/15/lg-1730sf-on-ubuntu-10-04](http://www.viitalat.net/index.php/htpc/2010/07/15/lg-1730sf-on-ubuntu-10-04)
Does that help?

---

### Post by xapient on 2010-08-30
unfortunately this website was one of the first sites i found.. therefore i already tried evtouch and editing the evtouch.conf (in ubuntu its located here: /usr/share/X11/xorg.conf.d/) -- pointed to the right device i get the error.. 

if left untouched it thinks the two event devices are the touchscreen and then configures the two (wich are actually IR devices) with evtouch ?!?

---

### Post by macrules on 2010-08-30
you might just need to remove evtouch?
I can't really help any further i guess, i have different hardware and I am working with a developer to get a custom driver.
Just google the errors you encounter.
Check /var/log/Xorg.0.log too and dmesg / /var/log/messages .

good luck!

---

### Post by xapient on 2010-08-30
sure.. thx anyway... 

just for information:  i tried to configure it with evdev too...  i tried to unload evdev, evtouch and load usbtouchscreen module..  no chance.. i also added usbhid quirks so the usbhid driver won't catch the touchscreen... nothing works..  if usbhid does not catch the touchscreen - noone does..

---

### Post by xapient on 2010-11-05
'''There is SOME progress on this topic but the Finger vu 706 touchscreen is still not working in Kubuntu 10.10 Maveric Meercat!'''  :!: 

I found out that the first problem is the "usbtouchscreen" module - it won't grab the new soundgraph device as the ID is not listed in the module.
I managed to get "usbtouchscreen" to grab the soundgraph device... but... even then "usbhid" grabs it first - this needs a workaround like an > usb quirk - kernel parameter < or simlpy load the usbtouchscreen module right before usbhid. (through ssh no big problem)


here is what i did and as much info i can provide! (i tried to sort out irrelevant information)


```
# sudo modprobe usbtouchscreen
# dmesg

usbcore: registered new interface driver usbtouchscreen

```

```

#  usb-devices 

T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=15c2 ProdID=3480 Rev=22.68
S:  Manufacturer=SoundGraph,Inc.---
S:  Product=SoundGraph.Inc
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)

```



```
# sudo sh -c "echo 15c2 3480 > /sys/bus/usb/drivers/usbtouchscreen/new_id"

# dmesg

input: SoundGraph,Inc.--- SoundGraph.Inc as 
/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.0/input/input14
input: SoundGraph,Inc.--- SoundGraph.Inc as 
/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.1/input/input15
input: SoundGraph,Inc.--- SoundGraph.Inc as 
/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.2/input/input16
```





```
#  usb-devices 

T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=15c2 ProdID=3480 Rev=22.68
S:  Manufacturer=SoundGraph,Inc.---
S:  Product=SoundGraph.Inc
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbtouchscreen
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=usbtouchscreen
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbtouchscreen
```





```
# cat /proc/bus/input/devices 

I: Bus=0003 Vendor=15c2 Product=3480 Version=2268
N: Name="SoundGraph,Inc.--- SoundGraph.Inc"
P: Phys=usb-0000:00:04.1-6.2/input0
S: 
Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.0/input/input14
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3

I: Bus=0003 Vendor=15c2 Product=3480 Version=2268
N: Name="SoundGraph,Inc.--- SoundGraph.Inc"
P: Phys=usb-0000:00:04.1-6.2/input0
S: 
Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.1/input/input15
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3

I: Bus=0003 Vendor=15c2 Product=3480 Version=2268
N: Name="SoundGraph,Inc.--- SoundGraph.Inc"
P: Phys=usb-0000:00:04.1-6.2/input0
S: 
Sysfs=/devices/pci0000:00/0000:00:04.1/usb1/1-6/1-6.2/1-6.2:1.2/input/input16
U: Uniq=
H: Handlers=mouse2 event4 
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3
```


```

# ls /dev/input/by-id/ -l

lrwxrwxrwx 1 root root 9 2010-11-05 20:36 usb-SoundGraph_Inc.---
_SoundGraph.Inc-event-if00 -> ../event2
lrwxrwxrwx 1 root root 9 2010-11-05 20:36 usb-SoundGraph_Inc.---
_SoundGraph.Inc-event-if01 -> ../event3
lrwxrwxrwx 1 root root 9 2010-11-05 20:36 usb-SoundGraph_Inc.---
_SoundGraph.Inc-event-if02 -> ../event4
```




```
#cat /etc/X11/xorg.conf


Section "InputDevice"
        Identifier "touchscreen"
        Driver  "evtouch
        Option  "Device" "/dev/input/event2"
        Option  "ReportingMode" "Raw"
        Option  "SHMConfig" "on
        Option  "Emulate3Buttons"
        Option  "Emulate3Timeout" "50"
        Option  "SendCoreEvents"
        Option  "MinX" "200"
        Option  "MinY" "400"
        Option  "MaxX" "4000"
        Option  "MaxY" "4000"
EndSection    


Section "ServerLayout"
        Identifier      "Server Layout"
        Screen          "DisplayLinkScreen"
        InputDevice "touchscreen" "CorePointer"
EndSection
```



```
#cat /var/log/Xorg.0.log


[  3554.924] State: S_UNTOUCHED Action: No Action               Button: 0
[  3554.925] State: S_TOUCHED   Action: No Action               Button: 0
[  3554.925] State: S_LONGTOUCHED       Action: down            Button: 1
[  3554.925] State: S_MOVING    Action: No Action               Button: 0
[  3554.925] State: S_MAYBETAPPED       Action: click           Button: 1
[  3554.925] State: S_ONEANDAHALFTAP    Action: down            Button: 3
[  3554.925] (**) Option "MinX" "200"
[  3554.925] (**) Option "MaxX" "4000"
[  3554.925] (**) Option "MinY" "400"
[  3554.926] (**) Option "MaxY" "4000"
[  3554.926] (**) Option "Emulate3Buttons"
[  3554.926] (**) Option "Emulate3Timeout" "50"
[  3554.926] (**) Option "SendCoreEvents"
[  3554.926] (**) Option "CorePointer"
[  3554.926] (**) EVTouch TouchScreen: always reports core events
[  3554.926] (II) XINPUT: Adding extended input device "EVTouch TouchScreen" 
(type: TOUCHSCREEN)
[  3554.927] (**) Option "Device" "/dev/input/event2"
[  3554.970] (II) EVTouch TouchScreen: Found absolute axes
```



While touching the screen there is no pointer movement whatsoever. moreover i tried to "cat" the device and testet event2,3,4 but i couldn't get any output :(



```
# cat /dev/input/event2 

-nothingatall-
```

so i'm stuck again.
 :roll:

---

### Post by xapient on 2010-11-06
there is something odd i noticed..   :confused:
there are 3 hid compliant devices with the same id... 2 for the imon remote and 1 composite device for the touchscreen...   when usbtoucscreen is loaded and the id written in /sys/bus/usb/drivers/usbtouchscreen/new_id then all 3 devices are claimed by usbtouchscreen..   (then event2 event3 and event4 devices exist)

same goes for lirc-imon

```

sudo modprobe lirc-imon
sudo sh -c "echo 15c2 3480 > /sys/bus/usb/drivers/lirc_imon/new_id"
```$ usb-devices

```
T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=15c2 ProdID=3480 Rev=22.68
S:  Manufacturer=SoundGraph,Inc.---
S:  Product=SoundGraph.Inc
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=lirc_imon
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon

```after this lirc0 lirc1 lirc2 devices exist..

so it has to be possible to get if0 and if1 to be claimed by lirc-imon and if2 by usbtouchscreen

and why has the other device also 2 IF's?
Vendor=17e9 ProdID=401c

I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=udlfb
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


is it possible that the touchinput comes over If1 from 17e9:401c ? i managed to get usbtouchscreen to grab this particular device and did a "sudo cat /dev/input/event2" and a "sudo cat /dev/input/mouse0" on the 2 new devices while touching the screen... 

-nothingatall-

still no progress in this case (but i am learning a lot about this stuff ^^)

:confused:


[COLOR=Purple]**EDIT:  there IS some progress again !!!**[/COLOR]

```
cat /dev/lirc1 
```

showed  > &#65533;&#65533;&#65533;&#65533;2K&#65533;&#65533;&#65533;&#65533;&#65533;>I&#65533;&#65533;&#65533;&#65533;&#65533;DH&#65533;&#65533;&#65533;&#65533;&#65533;DH&#65533;&#65533;&#65533;2K&#65533;&#65533;&#65533;2K&#65533;&#65533;&#65533;2K&#65533;&#65533;&#65533;"$&#65533;&#65533;&#65533;"$&#65533;&#65533;&#65533;"$&#65533;&#65533;&#65533;^C
while pressing buttos on the remote.. (irw says nothing and without lircd irrecord says 

> irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/lirc1 is 250
irrecord: LIRC major number is 61
irrecord: check if /dev/lirc1 is a LIRC device

---

### Post by xapient on 2010-11-07
Just some information from soundgraph forums about the IR devices:

> **4. iMON HW using HID Keyboard and Mouse driver**
- Our recent iMON products use HID Keyboard and Mouse driver.
- Some buttons on the remote can&#8217;t be checked through this API if it is  pressed or released. The reason is that these buttons are always  processed directly through HID Keyboard and Mouse driver. 
- These buttons are Pad button in mouse mode, L. Click, R. Click, Enter,  Back, Esc, Space, Menu, Windows and numeric buttons on iMON Pad remote,  Back, Menu and Enter buttons on iMON Mini remote and Back, Enter,  Up/Down/Left/Right and numeric buttons on MCE remote.


> 
FingerVU is an USB composite device. This composite device consists of  HID keyboard device, HID mouse device and HID compliant device. HID  keyboard/mouse driver are used for IR input from remote control. The  touch data is transferred through HID compliant device driver. If you'd  like to get data from FingerVU touch panel, you might need to check this  device.


so it looks like usb-hid should grab it in the first place - keyboard&mouse for IR and the composite device for TOUCH  - but what now? developers please find this thread ^^:KS

---

### Post by Ayuthia on 2010-11-07
Have you checked to see if you are getting any information from /dev/hidrawX (where X is  number between 0-9)?

---

### Post by xapient on 2010-11-07
oke .. i checked /dev/hidrawX  (0 to 7)  

hidraw0  mouse
hidraw1
hidraw2 keyboard
hidraw3
hidraw4
hidraw5 
hidraw6 3buttons of my IR
hidraw7 IR  ... AND TOUCHSCREEN 

wow !  the first time i see at least something happening when touching the screen.. its feels like my birthday ^^  thank you :)

i am a little confused that hidraw7 paints symbols to stout while pressing buttons on the IR because it does that for the touchscreen too...  

does this mean we have to use the usbhid for this device? 

[I]evtouch says this when pointing it to event5: 
EVTouch TouchScreen: Found 274 mouse buttons
nothing special when pointing it to event4
and its crashing xorg when pointing to mouse1[/I]
(those are the 3 soungraph devices)

---

### Post by Ayuthia on 2010-11-08
> **xapient said:**
> oke .. i checked /dev/hidrawX  (0 to 7)  

hidraw0  mouse
hidraw1
hidraw2 keyboard
hidraw3
hidraw4
hidraw5 
hidraw6 3buttons of my IR
hidraw7 IR  ... AND TOUCHSCREEN 

wow !  the first time i see at least something happening when touching the screen.. its feels like my birthday ^^  thank you :)

i am a little confused that hidraw7 paints symbols to stout while pressing buttons on the IR because it does that for the touchscreen too...  

does this mean we have to use the usbhid for this device? 

[I]evtouch says this when pointing it to event5: 
EVTouch TouchScreen: Found 274 mouse buttons
nothing special when pointing it to event4
and its crashing xorg when pointing to mouse1[/I]
(those are the 3 soungraph devices)

It does mean that you will need to have usbhid running or else the information will not be read.  hidraw is the information that is coming from the kernel module.  From what I can tell, it is from the [imon.ko module]("https://patchwork.kernel.org/patch/82119/").  However, I am not 100% sure of it.  The 15c2 vendor matches up, but I can't seem to find the next set of numbers (it might help to see the results of lsusb).

You might try going to the Console (via Control-Alt-F2 -- Control-Alt-F7 should take you back) and try using evtest.  You will most likely need to install it first.  Then you can run it:
```

sudo evtest /dev/input/event2

```
and touch the screen.  If it shows any input, then that is the event that you need for the touchscreen.  If it doesn't, you will probably want to try event3 and 4.  If one of them does produce results, you can post them here to see if anyone can help further.  

I did find another [link]("http://venky.ws/forums/viewtopic.php?f=2&t=315") where the person used a different driver.  It looked like he had some problems with the evtouch driver also.  It was for a different product so I am not for sure if it will work for you.

---

### Post by xapient on 2010-11-08
with **usbhid** 3 soundgraph devices are created *event4 event5 mouse1*

so i tried evtest with event4 and event5:
event4 is definitely a mouse.. there is left button, wheel, x, y etc.
*while touching the screen nothing happens..*
event5 is interpreted as keyboard.. there are over 200 buttons.. enter, a,b,c, etc.
*while touching the screen nothing happens either..*

(one interesting thing is, that 3 buttons of the remote generated some output on event5 - they were interpretet as backslash, enter, and something i forgot ^^ )


just to be sure i tried the same thing with the "**usbtouchscreen**" module.. 3 devices were createtd: *event2 event3 event4  *
evtest now sees those 3 as very identical touchscreen devices but touching the screen does nothing
_______________
i already found the driver from your link (plpevtch) but since there is nothing coming out of /dev/input/eventX the problem seems to be at a lower level than the xorg driver.. right?

thank you for your time :)

EDIT: do you think i should try the **lirc_imontouch** module from your link instead of *usbtouchscreen* or *usbhid* - could it be possible that the touchscreen input has to be interpreted by lirc (maybe with lircmd (mousedaemon))  
man.. what kind of device did i buy ^^  ah.. right ID 15c2:3480 SoundGraph Inc. ;)

---

### Post by Ayuthia on 2010-11-08
So it is a 15c2:3480.  From the imon.c code, it does not look like your device is in there so your device would not be recognized in there.  However, I think that code is most likely the closest to match your device.

You might check with Jarod Wilson <jarod@wilsonet.com> who is listed in the source code for imon.c and he might be able to help further.

The other option if you know how to compile kernel modules is to try and add your device to the imon.c code (it looks like it might just be a two line code change).

From what I can tell, the touch data is making it through usbhid but there are currently no kernel modules that can figure out what to do with that data so it is being ignored and not passed through to the /dev/input/event.

---

### Post by xapient on 2010-11-08
thx.. i was already in touch with jarod wilson and christoph bartelmus - thats why i wrote the device id into lirc_imon and compiled it..  sadly lirc_imon was no help.. but i learned a lot since my last try... so i am going for lirc_imontouch and i will report here...  (may take some time because of other things i have to do)

:KS
thx again!

---

### Post by Babitom on 2011-04-05
Hello, 

did you get your touch-display to work?
I recently bought a finger vu 895 touchscreen and I am trying since a few weeks to get the touch-function working.

When activating the screen i only get entries dev/hidraw5 and dev/usb/hiddevx (x..number), but no event-entry. Maybe there are still some faults in the xorg.conf.

I am fairly new to Ubunutu-Linux, so could you tell me how you checked the hidraw-input?
I saw that some guys just typed the hidraw-device into their xorg.conf and it seems to be working.


Thanks!

---

