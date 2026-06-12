---
title: "IR remote control on HP Pavilion dv6?"
date: 2010-07-25
forum: Hardware
---

### Post by Entheogen on 2010-07-25
Hi, 
I cannot find any tutorial for setting up ir remote control for my HP pavilion dv6 so I would like to know if its possible to make it work?
I've installed lirc and lirc-gnome-properties and here's what I get:
[IMG]http://img137.imageshack.us/img137/9395/screenshotjq.png[/IMG]
when I press buttons on remote nothing happens, but when i press one button in particular (right next to Windows media button) i can see cursor blinking! but it blinks only on that button.
here's the remote:
[IMG]http://lookness.com/upload/224/hp_pavilion_dv7-3160us_0.jpg[/IMG]
dmesg gives me nothing so I ran xev and I got this for mentioned button:
```
MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 36, synthetic NO, window 0x8600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x8600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967289 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,0), width 178, height 10, count 3

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,10), width 10, height 58, count 2

Expose event, serial 37, synthetic NO, window 0x8600001,
    (68,10), width 110, height 58, count 1

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,68), width 178, height 110, count 0

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,0), width 178, height 10, count 3

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,10), width 10, height 58, count 2

Expose event, serial 37, synthetic NO, window 0x8600001,
    (68,10), width 110, height 58, count 1

Expose event, serial 37, synthetic NO, window 0x8600001,
    (0,68), width 178, height 110, count 0

```

Only that button gives me output. It's recognized as XF86Display (same as Fn+F4) Any help please?

---

### Post by Entheogen on 2010-07-26
bump

---

### Post by regneva on 2010-07-26
Did you verify if lirc is set up right? When you execute "ps -ef | grep lirc" do you see lircd (lirc daemon) running? If yes, when you execute irw, can you see optput when you press keys?

---

### Post by Entheogen on 2010-07-26
yep, here's the output: 
```
goran@shiva:~$ ps -ef | grep lirc
root      1093     1  0 10:22 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/event6
goran    16700 16681  0 14:09 pts/0    00:00:00 grep --color=auto lirc
goran@shiva:~$ irw
00000000000100e3 00 KEY_SWITCHVIDEOMODE linux-input-layer
00000000000100e3 00 KEY_SWITCHVIDEOMODE linux-input-layer
00000000000100e3 00 KEY_SWITCHVIDEOMODE linux-input-layer
^C

``` 

only that display button is recognized. i read somewhere that on some HP Pavilion models I need to update bios in order to get ir remote working. Well I downloaded BIOS from HP's site for my laptop but I already had newest version.

---

### Post by regneva on 2010-07-26
It appears to me that your lircd.conf may be wrong and the code for only the display button is correct. I don't have any experience with HP notebooks, but you could try and search for lircd.conf for the same model. A quick search gave me these links : [http://linux.amazingdev.com/blog/archives/000921.html]("http://linux.amazingdev.com/blog/archives/000921.html") and [http://lirc.sourceforge.net/remotes/hp/]("http://lirc.sourceforge.net/remotes/hp/").

---

### Post by Entheogen on 2010-07-26
Thank you for links! I found codes for my remote ([http://lirc.sourceforge.net/remotes/hp/RC1762308-01B](http://lirc.sourceforge.net/remotes/hp/RC1762308-01B)). My lircd.conf had this line "include </etc/lirc/lircd.conf.gnome>" so I copied this conf to lircd.conf.gnome and now on irw I cannot see anything. I tried coping this conf to lircd.conf but nothing. I even did dpkg-reconfigure lirc but nothing. 
I have noticed that I need to select manually (with dpkg-reconfigure lirc) device /dev/input/event6, because with gnome-lirc i have /dev/input/event5 /dev/input/event7 and so on which doesn't give me any response to Display button, although I can see cursor blinking and 'xev' gives me output.

---

### Post by Entheogen on 2010-07-26
oh and here's my /proc/bus/input/devices
```
goran@shiva:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=20000 0 20 0 0 0 0 500f 2100003 3803078 f900d401 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=23
B: KEY=40 0 0 0 7 0 0 2100400 0 0 0 0
B: SW=22

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=0408 Product=03f1 Version=0104
N: Name="HP Webcam"
P: Phys=usb-0000:00:1d.7-4/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input8
U: Uniq=
H: Handlers=event8 js0 
B: EV=9
B: ABS=7

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse0 event9 
B: EV=b
B: KEY=420 0 30000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0001 Vendor=111d Product=7603 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=40001
B: SND=6

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Line Out at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: EV=21
B: SW=40

```
seems that there's no ir receiver.. And event6 is video bus (??)

---

### Post by regneva on 2010-07-26
Does the remote show up in lsusb? I'm guessing that internally the remote receiver is connected via USB. I'm asking this because, perhaps, your hardware.conf has some error?

Here are some parameters you may want to check.

```

REMOTE="Your remote name as it appears in lircd.conf, I think"
REMOTE_MODULES="lirc_dev lirc_atiusb" #assuming it is USB
REMOTE_DEVICE="correct device where it's read"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
START_LIRCD="true"
LOAD_MODULES="true"

```

Did you try to find hardware.conf that's been used by people successfully for your laptop model?

---

### Post by Entheogen on 2010-07-26
nope, there's nothing on lsusb:
```
goran@shiva:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I think that Quanta Computer, Inc. is webcam.
Here's lspci:
```


goran@shiva:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```
And here's lshal: [http://pastebin.com/YvwtyuM5](http://pastebin.com/YvwtyuM5)
hardware.conf:
```
goran@shiva:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="HP\ WMI\ hotkeys"
RECEIVER_VENDOR="Linux\ Input\ Device"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux\ Input\ Layer\ compatible\ Remote"
REMOTE_VENDOR="Generic"

```
i tried setting REMOTE_DRIVER to lirc_dev and lirc_i2a but I got some errors, and dmesg gives me nothing on lirc! 
```
goran@shiva:~$ sudo modprobe lirc
FATAL: Module lirc not found.
goran@shiva:~$ sudo modprobe lirc_dev
FATAL: Module lirc_dev not found.
goran@shiva:~$ dmesg | grep lirc
goran@shiva:~$ 

```

I think that lucid didn't recognize IR receiver, but I don't know how it can read Display command from remote. I googled for hardware.conf which will work for my remote but I didn't find nothing yet.
FYI I have 2.6.34-020634-generic kernel installed (with headers, of course) because my broadcom wlan didn't work with kernel found in Ubuntu repos. Nevertheless, as far as I remember remote didn't work on 2.6.33 kernel either.

---

### Post by Entheogen on 2010-07-26
**update:** I purged everything that had to do with lirc from apititude and installed lirc again, and followed this: [http://amodjaltade.blogspot.com/2009/05/hp-remote-control-in-ubuntu.html](http://amodjaltade.blogspot.com/2009/05/hp-remote-control-in-ubuntu.html)

Now i have lirc modules:
```
goran@shiva:~$ lsmod | grep lirc
lirc_serial             9923  0 
lirc_ene0100            6479  0 
lirc_dev                9022  2 lirc_serial,lirc_ene0100

```
and dmesg gives me output:
```
goran@shiva:~$ dmesg | grep lirc
[    5.747181] lirc_dev: IR Remote Control driver registered, major 61 
[    5.755400] lirc_dev: lirc_register_driver: sample_rate: 0
[   13.584532] lirc_serial: auto-detected active low receiver
[   13.584540] lirc_dev: lirc_register_driver: sample_rate: 0
[   13.584635] lirc_serial $Revision: 5.104 $ registered

```

even lshal gives me more:
```
goran@shiva:~$ lshal | grep lirc
  lirc.input.is_remote = false  (bool)
udi = '/org/freedesktop/Hal/devices/platform_lirc_serial_0'
  info.linux.driver = 'lirc_serial'  (string)
  info.product = 'Platform Device (lirc_serial.0)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_lirc_serial_0'  (string)
  linux.sysfs_path = '/sys/devices/platform/lirc_serial.0'  (string)
  platform.id = 'lirc_serial.0'  (string)

```
but I irw/xev doesnt give me any output. Now Display button doesn't work :/ 
I tried with lircd.conf for my remote and with lircd.conf from mentioned web site but with no luck

**UPDATE** I have response when I use mode2 -d /dev/lirc0 - a bunch of numbers: 
```

...
pulse 975
space 825
pulse 525
space 375
pulse 525
space 375
pulse 525
space 375
pulse 450
space 375
pulse 975
space 825
pulse 525
space 375
pulse 450
space 375
pulse 525
space 375
pulse 450

```
which seem arbitrary to me. irw and xev still give me nothing!
I set up new lircd.conf using irrecord and I got same conf file as I already downloaded for my remote, which means that all keycodes are recognized correct, but I still cannot see anything with xev/irw

---

### Post by Entheogen on 2010-07-27
bump

---

### Post by Entheogen on 2010-07-28
damn i need to bump again.. does anyone know what could be the problem?

---

### Post by Entheogen on 2010-07-31
bump... :(

---

### Post by Entheogen on 2010-08-12
**b**ring **u**p **m**y **p**ost :-k

---

### Post by tupikoff.ru on 2010-08-26
Hi!
I tune it on Kubuntu 10.04

You in the middle of the way )
Now you need:

**/etc/lirc/hardware.conf**

```
LOAD_MODULES=”true”
MODULES="lirc_ene0100"
LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_DEVICE="/dev/lirc0"
```

**/etc/lirc/lircd.conf** put content from this file:
[http://lirc.sourceforge.net/remotes/hp/RC1762308-01B](http://lirc.sourceforge.net/remotes/hp/RC1762308-01B)

When:
$ sudo /etc/init.d/lirc restart

$ irw


After i use kdelirc in KDE
It's very easy to tune.

---

### Post by Entheogen on 2010-08-26
IT WORKS! thank you so much :) 
Now I am having troubles with moovida media center, but I think I will find the answer.. or at least new media center, the main thing is working! :)

---

### Post by cyrex on 2010-08-26
Am also checking this out. Will try your method on ubuntu and see if it works.

---

### Post by Entheogen on 2010-08-28
Hi, 
I have some problems with Moovida now :/
I installed Moovida 1.09 and when I setup moovida.conf to use LIRC configuration file that I've created with setup_lirc.py.. Anyway when I try to start Moovida it freezes my computer. I tried switching to tty1 or other terminals, and I tried to switch on/off Caps and Num Lock keys but I cannot do anything (maybe a kernel panic). I didn't tried SysReq instructions so I don't know if the kernel recognizes them. I found out a workaround for this. I tried to start moovida with "PGM_DEBUG=pgm*:3 moovida > moovida.log 2>&1" and it started normally and remote control works perfectly. In the log files there are some python errors, but everything works fine. So I wanna know why it crashes my system when I try to start it regularly (with 'moovida' command)?

Next thing I wanna know is how to setup dual head monitors to work with moovida. Here's my situation:
I have ATI Radeon 4650HD gfx card and I connect second screen to VGA connector. I have fglrx driver installed and I have dual screens working great with "Multi-Display desktop with display(s)". I think that is something similar to nVidia's TwinView. Anyway I want to say that I don't use separate X screens so everything is on big virtual screen with 2646 x 1024 resolution which is separated for my monitors so I can drag windows across both of them. 
When I start Moovida with second screen connected I get zoomed in picture. I want to start it in full screen on secondary monitor, but when I drag Moovida to another screen and hit ESC to get in fullscreen, resolution of moovida is screwed up because it is confused of what real resolution of that screen is. [Here's screenshot.](http://img835.imageshack.us/img835/9783/screenshotmoovidamediac.png)
Can I fix this without setting separate X screens for dual-head setup?

---

