---
title: "iNexio USB Touch Screen"
date: 2010-08-22
forum: Hardware
---

### Post by saadakhtar on 2010-08-22
Hello all,
it has been a while i have visited the great ubuntu forums. Most of the basic stuff i do, i can manage to find enough information by reading posts on the web, searching around but sometimes i run into some mother of problems and here is one for the world this time. LOL

I have a USB Touch Screen Monitor and i would very much like the touch part to work on it.

Here is what i have gotten so far, by the way i am running ubuntu lucid lynx.

output for lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**_Bus 002 Device 042: ID 1870:0001  _**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0723 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


with no name or device name in front of it
Googled it around and found it to be (iNexio Co ltd) product 0001 (iNexio Touch Screen Controller)
the touch screen is connected via usb.

lsmod

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203170  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
i915                  283218  3 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
intel_agp              24473  2 i915
drm_kms_helper         29297  1 i915
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
drm                   163143  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
agpgart                31788  2 intel_agp,drm
video                  17375  1 i915
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
output                  1871  1 video
atl1c                  28307  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
usbhid                 36174  0 
hid                    67032  1 usbhid
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39457  0 

i added the inexio and usbtouchscreen modules to /etc/modules and rebooted. output of lsmod after the above action:

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203170  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
i915                  283218  3 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
intel_agp              24473  2 i915
drm_kms_helper         29297  1 i915
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
drm                   163143  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd_seq_midi            4557  0 
usbtouchscreen          8073  0 
snd_rawmidi            19056  1 snd_seq_midi
agpgart                31788  2 intel_agp,drm
video                  17375  1 i915
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
output                  1871  1 video
inexio                  1817  0 
atl1c                  28307  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
usbhid                 36174  0 
hid                    67032  1 usbhid
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39457  0 


now modules are present but not being used by anything.

i also found search results that led to pages with patch code that needs to be applied to the kernel for usbtouchscreen module to work (hotplug, reboots and stuff) with the iNexio touch screen correctly. All of this i can some how do but none of the posts say how to get the touch screen to work.

Can someone please help me with this issue, i would greatly appreciate it. Please understand that i am not looking for a hand out, i just need to be put to the right direction.

thank you

---

### Post by Zeddy on 2010-11-21
I'm having the same problem with Maverick 10.10 (release).

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1870:0001 Nexio Co., Ltd iNexio Touchscreen controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod:
Module                  Size  Used by
joydev                  8735  0 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
pcmcia                 35973  0 
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
i915                  290938  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 i915
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
inexio                  1829  0 
drm                   168054  4 i915,drm_kms_helper
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbtouchscreen         11169  0 
intel_agp              26360  2 i915
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
soundcore                880  1 snd
psmouse                59033  0 
serio_raw               4022  0 
led_class               2633  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
floppy                 54311  0 
e1000e                132956  0 


messages log (partial)
Nov 22 12:51:00 Maverick kernel: [   19.146094] Nexio device: m-NEXIO, firmware version: 2.00SMS
Nov 22 12:51:00 Maverick kernel: [   19.146229] input: iNexio iNexio USB as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4


udev log (partial):
KERNEL[1290394243.920610] add      /module/usbtouchscreen (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/usbtouchscreen
SUBSYSTEM=module
SEQNUM=1442

KERNEL[1290394243.920628] add      /bus/usb/drivers/usbtouchscreen (drivers)
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/usb/drivers/usbtouchscreen
SUBSYSTEM=drivers
SEQNUM=1450

KERNEL[1290394243.988772] add      /module/inexio (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/inexio
SUBSYSTEM=module
SEQNUM=1457

UDEV  [1290394243.989017] add      /module/inexio (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/inexio
SUBSYSTEM=module
SEQNUM=1457

KERNEL[1290394243.989087] add      /bus/serio/drivers/inexio (drivers)
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/serio/drivers/inexio
SUBSYSTEM=drivers
SEQNUM=1458

UDEV  [1290394243.989291] add      /bus/serio/drivers/inexio (drivers)
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/serio/drivers/inexio
SUBSYSTEM=drivers
SEQNUM=1458

/etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
usbtouchscreen
inexio


jockey.log  (for device ID 1870:0001)
HardwareID('modalias', 'usb:v1870p0001d0100dc02dsc00dp00ic02isc02ip00')
2010-11-22 12:52:14,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x99ebfcc> about HardwareID('modalias', 'usb:v1870p0001d0100dc02dsc00dp00ic0Aisc00ip00')
2010-11-22 12:52:14,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbtouchscreen', 'jockey_handler': 'KernelModuleHandler'}



I had this touchscreen working in June '10 with kernel 2.6.34-020634rc3-generic_2.6.34-020634rc3_i386, (it detected and connected at boot time with no tweaking) but now it doesn't seem to connect at all.

---

### Post by saadakhtar on 2010-11-26
hello,

this inexio touch panel was a real pain but i finally got it to work.
basically. its a single touch device plus the screen calibration is very much useless for it as it always seems to be off a inch or two.

i ended up getting a 46" pulseIR touch screen panel that supports multitouch.

however. here is the link to linux_updd driver that worked for me.

[http://tinyurl.com/26wmw9s](http://tinyurl.com/26wmw9s)

there is also a uk based company that makes opensource drivers for touch devices. check out [http://www.touch-base.com](http://www.touch-base.com)

hope this helps.

---

### Post by pisewip on 2011-06-23
Hi all,
I've a Nexio touch screen now working.
Really I've used a linux mint 11 but I think this approach would work in ubuntu 11 too.

You need a full installation of the distro (no boot option like irqpoll or noapic etc.) elsewhere you will encounter the problem the iNexio device is claimed end released and not associated to an input device.

Look my dmesg

```
[   17.936398] Nexio device: m-Nexio, firmware version: 2.10SMMN
[   17.936489] input: iNexio iNexio USB as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input4
[   17.936642] cdc_acm 6-1:1.0: This device cannot do calls on its own. It is not a modem.
[   17.936645] usbcore: registered new interface driver usbtouchscreen
[   17.936657] cdc_acm: probe of 6-1:1.0 failed with error -16
[   17.936702] usbcore: registered new interface driver cdc_acm
[   17.936704] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```

Here you can see the iNexio device is connected to the input device input4

Next to make it work you need to add to your /usr/share/X11/xorg.conf.d
a configuration file about the touch screen. I've called it 12-nexio.conf
```
Section "InputClass"
        Identifier "iNexio iNexio USB"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "Calibration" "0 128 0 104"
EndSection

```

You can obtain the Identifier entry using the command
```

evtest /dev/input/event4

```
which return
```

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x1870 product 0x1 version 0x100
Input device name: "iNexio iNexio USB"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value    104
      Min        0
      Max      128
    Event code 1 (Y)
      Value     66
      Min        0
      Max      104
Testing ... (interrupt to exit)

```
This command display the min max values for x and y axes.

... it is interactive command you will see output about cursor position if you touch the screen.

I've understood you can use the xinput_calibrator software if you demand the control of iNexio to evdev like you are doing in the xorg.conf.d configuration.

**Something about xinput**
using the command 
```
xinput list
```
you can obtain the list of your device including the iNexio device (for me it is the device number 10).
Before setting the xorg.conf.d file the output of the command
```
xinput list 10 --long
```
returned to me a Range under the axes label that was from 0 to 0.
In this way the behavior of the touch screen it was always point in 0,0 coordinates.
Only after setting the xorg.conf.d configuration file the output of 
```
xinput list 10 --long
```
return me a Range from 0 to something different from 0.

---

