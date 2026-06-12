---
title: "Acer Aspire 5100 webcam video very dark"
date: 2010-10-22
forum: Hardware
---

### Post by hjaddad on 2010-10-22
I've looked everywhere and even asked help on my local ubuntu forums but so far I've found no solution for this:

I have Ubuntu 10.10 i386 on my Aspire 5100 and when I try to view my webcam (ALi M5602) with *cheese*, *skype* or *gstreamer-properties* the image is VERY dark. 

The camera works, I can see bright lights in great detail but in normal lighting it almost impossible to see anything.


Here are some examples (the display of my phone set to maximum brightness!):

[IMG]http://dl.dropbox.com/u/119937/2010-10-17-003644.jpg[/IMG]
With default settings


[IMG]http://dl.dropbox.com/u/119937/2010-10-17-135214.jpg[/IMG]
With **v4lctl bright 200** (same result with other brightness settings)

lsusb
```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod | grep m5602
```

gspca_m5602 * * * * * *52354 *0 
gspca_main * * * * * * 23644 *1 gspca_m5602

```

v4lctl -c /dev/video0 list
```

ioctl: VIDIOC_G_STD(std=0x804f07bbf8e4c38 [PAL_H,PAL_I,PAL_D,PAL_Nc,PAL_60,?,SECAM_D,SECAM_G,SECAM_H,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
attribute *| type * | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm * * * | choice | (null) *| (null) *|
input * * *| choice | ALi m56 | ALi m56 | ALi m5602
bright * * | int * *| * * 126 | * * 126 | range is 0 => 255
Whitebalan | bool * | off * * | off * * |
Gamma (sof | int * *| * *1000 | * *1000 | range is 500 => 3000
exposure * | int * *| * * * 0 | * * * 0 | range is 0 => 60
gain * * * | int * *| * * 113 | * * 113 | range is 0 => 255
horizontal | bool * | off * * | off * * |
vertical f | bool * | off * * | off * * |

```


When I still had Windows a couple of weeks ago, the image was just fine so I don't think it is hardware failing. It seems it just needs some gain or exposure, but how can I set those? 

For example **v4lctl gain 200** gives error *no handler for gain* :(

In *gstreamer-properties*, if I select the older *Video for Linux* version, I get only green image...

---

### Post by utilitytrack on 2010-10-23
Hello!

As I see, **hjaddad**, you are second man who get this webcam (0402:5602) working with latest versions of kernel, what in itself is amazing. Can you please provide here some diagnostic info for help us to resolve a 16575 Kernel Bug? It's here: **"ALi Corp. 5602 (m5602) webcam not working on newest kernels (2.6.31, 2.6.32, 2.6.35)"**([https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575"))

You can ask Mr. **[titomax82]("http://ubuntuforums.org/member.php?u=1120135")** about he own experience. He uses a **Packard Bell EasyNote MX67** laptop with exactly the same webcam (0402:5602). On this forum some time ago it was a whole saga to make this camera worked: [http://ubuntuforums.org/showthread.php?t=1541620]("http://ubuntuforums.org/showthread.php?t=1541620"). As a result of many scientific studies revealed that there is some regressions in driver functionality on newer kernels.
As you can see, on this issue **titomax82** opened a new ticket on Kernel Bugzilla. Now, I think, **titomax82** can do lecture on how to deal with this webcam. 

So, we want to know your experience. May be it's will help to troubleshoot your problems also.

What exactly needed? Open the terminal, type these commands and provide outputs here.
```
$ uname -r
$ lspci -nn
# lsmod | grep -E 'cam|video|gspca'
# lsusb -v -s 001:003
$ grep -e video /etc/group
$ dmesg | grep -E -i 'cam|video|gspca|5602|ISOC'
$ ls -l /dev/video*
$ ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*
$ cat /proc/bus/input/devices
$ v4l-info
$ dpkg -l libv4l\* | tail -1
$ dmesg > dmesg_full.log

```
Please attach file dmesg_full.log to post.

Also please describe what you see after this:
```
$ mplayer tv:// -tv driver=v4l2:device=/dev/video0
```

[SIZE="1"]Note: don't forget that commands beginning from '#' character need to execute from root. [/SIZE]

> **hjaddad said:**
> The camera works, I can see bright lights in great detail but in normal lighting it almost impossible to see anything.

I will not make unwarranted conclusions, but it seems that it's another bug in gspca_m5602 module. Help us to find it!

Thanks

---

### Post by titomax82 on 2010-10-23
maybe it's a different sensor...waiting for outputs...

---

### Post by hjaddad on 2010-10-24
I run *apt-get upgrade* and installed a load of updates and now surprisingly the image seems a lot better! It's still a bit dim and flickering on fluorescent lamp light, but looks quite good..


But anyway, this is what I got with your commands. Hope it helps someone:

```

root@Aspire5100:~# uname -r
2.6.35-22-generic



root@Aspire5100:~# lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)



root@Aspire5100:~# lsmod | grep -E 'cam|video|gspca'
gspca_m5602            52354  0 
gspca_main             23644  1 gspca_m5602
videodev               43098  1 gspca_main
v4l1_compat            13359  1 videodev
video                  18712  0 
output                  1883  1 video



root@Aspire5100:~# lsusb -v -s 001:003



root@Aspire5100:~# grep -e video /etc/group
video:x:44:user,friends



root@Aspire5100:~# dmesg | grep -E -i 'cam|video|gspca|5602|ISOC'
[    0.344000] pci 0000:01:05.0: Boot video device
[   20.346865] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1f/LNXVIDEO:00/input/input6
[   20.347173] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.428745] Linux video capture interface: v2.00
[   20.483554] gspca: main v2.9.0 registered
[   20.485989] gspca: probing 0402:5602
[   20.485997] ALi m5602: Probing for a po1030 sensor
[   20.539326] ALi m5602: Probing for a mt9m111 sensor
[   20.559180] ALi m5602: Probing for a s5k4aa sensor
[   20.712077] ALi m5602: Probing for an ov9650 sensor
[   21.272042] ALi m5602: Sensor reported 0xffff
[   21.272048] ALi m5602: Probing for a s5k83a sensor
[   21.352680] ALi m5602: Detected a s5k83a sensor
[   21.426337] gspca: video0 created
[   21.426370] usbcore: registered new interface driver ALi m5602
[   21.426373] ALi m5602: registered
[ 9980.488390] gspca: ISOC data error: [0] len=754, status=-71
[ 9980.860707] ALi m5602: Camera was flipped
[ 9986.465517] ALi m5602: Camera was flipped



root@Aspire5100:~# ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2010-10-24 11:01 /dev/video0



root@Aspire5100:~# ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*
lrwxrwxrwx 1 root root 12 2010-10-24 11:01 /dev/v4l/by-id/usb-0402_USB2.0_Camera-video-index0 -> ../../video0
lrwxrwxrwx 1 root root 12 2010-10-24 11:01 /dev/v4l/by-path/pci-0000:00:13.2-usb-0:4:1.0-video-index0 -> ../../video0



root@Aspire5100:~# cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

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
H: Handlers=sysrq kbd event4 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=045e Product=0029 Version=0100
N: Name="Microsoft Microsoft IntelliMouse® Optical"
P: Phys=usb-0000:00:13.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb2/2-4/2-4:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1f/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=12b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=6420 0 3000f 0 0 0 0 0 0 0 0
B: ABS=11000003



root@Aspire5100:~# v4l-info

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "ALi m5602"
	card                    : "USB2.0 Camera"
	bus_info                : "usb-0000:00:13.2-4"
	version                 : 2.9.0
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "ALi m5602"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "BA81"
	pixelformat             : 0x31384142 [BA81]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 640
	fmt.pix.height          : 480
	fmt.pix.pixelformat     : 0x31384142 [BA81]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 640
	fmt.pix.sizeimage       : 307200
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "brightness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 126
	flags                   : 32

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "USB2.0 Camera"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 640
	maxheight               : 480
	minwidth                : 48
	minheight               : 32

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "ALi m5602"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
    VIDIOCGAUDIO
	audio                   : 0
	volume                  : 0
	bass                    : 0
	treble                  : 0

picture
    VIDIOCGPICT
	brightness              : 32382
	hue                     : 0
	colour                  : 0
	contrast                : 0
	whiteness               : 0
	depth                   : 8
	palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 640
	height                  : 480
	chromakey               : 0
	flags                   : 0



root@Aspire5100:~# dpkg -l libv4l\* | tail -1
ii  libv4l-0                              0.6.4-1ubuntu1                                    Collection of video4linux support libraries


```


Attached is **dmesg_full.log**


**mplayer tv:// -tv driver=v4l2:device=/dev/video0** won't display anything, just gives this:
```
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB2.0 Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = ALi m5602;
 Current input: 0
 Current format: unknown (0x31384142)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Cannot find codec matching selected -vo and video format 0x31384142.
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 2 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
```



**[COLOR="Red"]EDIT:[/COLOR]**

It seems the webcam had changed its USB port also, here are results for
**lsusb -v -s 001:00[COLOR="red"]2[/COLOR]**:

```
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x5602 M5602 Video Camera Controller
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB2.0 Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          101
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by utilitytrack on 2010-10-24
**hjaddad**

Thanks for your complete information! Very good!

I discovered that core module (gspca_main) of your webcam driver reported this:
```
[ 9980.488390] gspca: ISOC data error: [0] len=754, status=-71
```

Here is the people with exactly the same hardware and with the same error in logs: [https://bugzilla.kernel.org/show_bug.cgi?id=15651]("https://bugzilla.kernel.org/show_bug.cgi?id=15651") And as result they wrote that camera don't work, but at the time yours camera is properly functioning... So, now for me it's clearly that this message is not the reason of they problems. 

**hjaddad**, I could ask you to create account on Kernel Bugzilla and write comment to bug 16575 that I mentioned above? ([https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575")) Your experience is important. Thank you.

---

### Post by titomax82 on 2010-10-25
My webcam doesn't work even in 10.10 and I notice my lsusb is slight different:
 
Bus 001 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller
 
insted of:
 
Bus 001 Device 003: ID 0402:5602 ALi Corp. M5602 Video Camera Controller

the second (not mine) is more specific....

---

