---
title: "xgalax driver problem"
date: 2009-05-21
forum: Hardware
---

### Post by genericUserName on 2009-05-21
Hi, i'm preparing an ePOS (electronic point of sale) deployment and i've been tasked with feasability testing of linux on the clients (the servers will 

be linux and there are obvious advantages to a homogeneous network). With the exception of touch-screen functionality (Hyundai G50TR) we've got 

everything working fine. The hardware is known good (the machine currently dual boots windows / ubuntu) so i'm baffled as to why it doesn't work.

Ubuntu 9.04
Kernel 2.6.28-11
Driver [http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/2.06.2416/TouchKit-2.06.2410-32b-k26.tar.gz](http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/2.06.2416/TouchKit-2.06.2410-32b-k26.tar.gz)

The touch component of the monitor is connected via USB, on running lsusb I get the output:

```
test@test-desktop:~/Desktop/TouchKit32$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Running sudo cat /dev/usb/hiddev0 shows the data data being recieved from clicks / movement.



Installation procedure:

Download and extract driver
Execute setup script:

```
test@test-desktop:~/Desktop/TouchKit32$ sudo ./setup.sh


(*) Linux driver installer for TouchKit controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the TouchKit driver.
(I) Found and removed previous TouchKit driver.
(I) Extract TouchKit driver archive to /usr/local/TouchKit32.
(I) Create TouchKit utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 6.9.0 ~ 7.2.0
(I) Copy X module: x69/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 3
(I) Using interface: USB
(I) Found a HID compliant touch controller.

(I) Found X configuration file: /etc/X11/xorg.conf.
(I) Add touch configuration into /etc/X11/xorg.conf.
(W) No "ServerLayout" section found! It will be appended automatically.

(I) Please reboot the system for some changes to take effect.
(I) After booting, type "TouchKit" to do calibration.

test@test-desktop:~/Desktop/TouchKit32$
``` 


The machine was then rebooted, on attempting to launch the TouchKit configuration utility the error message "No Touch Controller found." appears. As far 

as I can tell the files are all in the correct places (driver in /usr/local/xorg/includes/input/) and xorg is configured correctly (xorg.conf follows)


```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
	Screen	"Default Screen"
        InputDevice "EETI" "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"		# Also tried "hiddevs", "/dev/usb/hiddev0"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
```


Finally, I run the configuration application with root priveleges:


```
test@test-desktop:~/Desktop/TouchKit32$ sudo TouchKit
```


The application loads and throws the error message "No Touch Controller found."

As far as I can tell there's no error log for the driver itself and i've reached a brick wall as far as my own expertise with this stuff goes, any assistance in getting this hardware to work would be greatly appreciated.

---

### Post by genericUserName on 2009-05-24
Just a note for anyone having similar issues with the egalax driver, downgrading the system to ubuntu 8.04 allowed me to get the touchscreen to work correctly, i've also submitted a bug report to the developers.

---

### Post by h0dges on 2009-06-28
Hi,

Just wondering what the situation is with this bug as I'm experiencing it too with a non-HID touchscreen. The touchscreen itself works (it registers movement in trackpad style) but i cannot get the TouchKit utility or calibration tools working; just the same error as you receive.

---

### Post by Klondike on 2009-07-09
I'm about to try this out, I just bought one of these, and a note - they have newer (beta) drivers published in May, newer than the one you linked to in the original post.

Driver homepage:
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

---

### Post by Klondike on 2009-07-09
I was able to get this working on my Ubuntu 9.04 box the first time, using the newer beta drivers. I didn't try the older ones.

---

### Post by h0dges on 2009-07-12
Ok I installed the newest drivers and can get the eGalaxTouch configuration utility to load. It recognises the touch device but the device itself still acts as a mouse.

Terminal response during installation:

```

    matt@matt-linux:~/Downloads/eGalaxTouch32$ sudo sh setup.sh
    [sudo] password for matt:

    (*) Linux driver installer for eGalax Touch controller

    (I) Check user permission: root, you are the supervisor.
    (I) Begin to setup the eGalax Touch driver.
    (I) Found and removed previous eGalax Touch driver.
    (I) Extract eGalax Touch driver archive to /usr/local/eGalaxTouch32.
    (I) Create eGalaxTouch utility shortcut in /usr/bin.
    (I) Create TKCal tool shortcut in /usr/bin.
    (I) Check X window version: 1.6.x
    (I) Copy X module: x16/egalax_drv.so to /usr/lib/xorg/modules/input.

    (Q) Which interface controller do you use?
    (I) [1] RS232 [2] PS/2 [3] USB : 3
    (I) Using interface: USB
    (I) Found a non-HID compliant touch controller.
    (I) Note that the option "Device" "/dev/input/mice" for mouse
        should be changed to "Device" "/dev/input/mouseX" to prevent
        the mouse driver from reading.
    (I) For details, see the document "Driver Guide.pdf".

    (I) Found X configuration file: /etc/X11/xorg.conf.
    (I) Removed touch configuration from /etc/X11/xorg.conf.
    (I) Add touch configuration into /etc/X11/xorg.conf.
    (W) No "ServerLayout" section found! It will be appended automatically.

    (I) Please reboot the system for some changes to take effect.
    (I) After booting, type "eGalaxTouch" to do calibration.

    matt@matt-linux:~/Downloads/eGalaxTouch32$
```

I rebooted but touchscreen still acted as mouse. so I added these lines to xorg.conf (as per the instructions):

```
Section "InputDevice"
     Identifier "Mouse0"
     Driver "mouse"
     Option "Device" "/dev/input/mouse2"
EndSection
```

Still no effect.

Typing lsusb I get:

```
matt@matt-linux:~$ lsusb
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 004: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 001 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Typing 'cat /proc/bus/input/devices' I get:

```
matt@matt-linux:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.7-4.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.4/1-4.4:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=400 0 0 0 0 0 0 0 0 0 0
B: ABS=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=0c45 Product=62c0 Version=0100
N: Name="USB 2.0 Camera"
P: Phys=usb-0000:00:1d.7-5
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input9
U: Uniq=
H: Handlers=event9 
B: EV=3
B: KEY=1 0 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

```

As you can see, the touchscreen has been assigned the handler 'mouse1' whereas the actual trackpad on this laptop is assigned 'mouse2'.

Help!

---

### Post by jchau on 2010-01-11
h0dges,

In the eGalaxTouch utility, in the "Misc" tab, there is a "Mouse mode" setting that you can use to make the touchscreen behave more like a touchscreen and less like a mouse.  

Try changing it to "Click on Touch" or "Click on Release".

---

