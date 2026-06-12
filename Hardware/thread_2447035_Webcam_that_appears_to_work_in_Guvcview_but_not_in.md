---
title: "Webcam that appears to work in Guvcview but not in Cheese or Skype"
date: 2020-07-11
forum: Hardware
---

### Post by aquaduck on 2020-07-11
Hi,

I have a webcam that appears to work in Guvcview but not in Cheese or Skype. If anyone could shed some light on what I'm doing wrong here that would be great!

Thanks,
AD

```
dave@gigabyte:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.4 LTS"
```

```
dave@gigabyte:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:0929 Logitech, Inc. Labtec Webcam Pro
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
dave@gigabyte:~$ lsmod
Module                  Size  Used by
cmac                   16384  1
arc4                   16384  0
md4                    16384  0
nls_utf8               16384  4
cifs                  737280  5
ccm                    20480  0
fscache                65536  1 cifs
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             217088  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
kvm                   614400  1 kvm_intel
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_intel          45056  6
gspca_spca561          20480  0
crct10dif_pclmul       16384  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
gspca_main             36864  1 gspca_spca561
crc32_pclmul           16384  0
v4l2_common            16384  1 gspca_main
videodev              184320  3 gspca_main,v4l2_common,gspca_spca561
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
media                  40960  1 videodev
pcbc                   16384  0
input_leds             16384  0
aesni_intel           188416  1
snd_hwdep              20480  1 snd_hda_codec
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
glue_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
intel_cstate           20480  0
intel_rapl_perf        16384  0
intel_wmi_thunderbolt    16384  0
mei_me                 40960  0
mei                    94208  1 mei_me
shpchp                 36864  0
acpi_pad              180224  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
mxm_wmi                16384  0
i915                 1622016  24
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
drm                   401408  16 drm_kms_helper,i915
ahci                   40960  1
libahci                32768  1 ahci
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi
video                  45056  1 i915

```

```
dave@gigabyte:~$ ls -ltr /dev/video*
crw-rw----+ 1 root video 81, 0 Jul 11 13:16 /dev/video0
```

```
root@gigabyte:/var/log# find /usr/lib -iname '*v4l*'
/usr/lib/i386-linux-gnu/libv4lconvert.so.0
/usr/lib/i386-linux-gnu/libv4l2.so.0.0.0
/usr/lib/i386-linux-gnu/libv4l2.so.0
/usr/lib/i386-linux-gnu/libv4lconvert0
/usr/lib/i386-linux-gnu/libv4l1.so.0.0.0
/usr/lib/i386-linux-gnu/libv4lconvert.so.0.0.0
/usr/lib/i386-linux-gnu/libv4l
/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
/usr/lib/i386-linux-gnu/libv4l/plugins/libv4l-mplane.so
/usr/lib/i386-linux-gnu/libv4l1.so.0
/usr/lib/rpm/platform/armv4l-linux
/usr/lib/x86_64-linux-gnu/libv4lconvert.so.0
/usr/lib/x86_64-linux-gnu/libv4l2.so.0.0.0
/usr/lib/x86_64-linux-gnu/libv4l2.so.0
/usr/lib/x86_64-linux-gnu/libv4lconvert0
/usr/lib/x86_64-linux-gnu/libv4l1.so.0.0.0
/usr/lib/x86_64-linux-gnu/libv4lconvert.so.0.0.0
/usr/lib/x86_64-linux-gnu/libv4l
/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/plugins/libv4l-mplane.so
/usr/lib/x86_64-linux-gnu/libv4l1.so.0
```

```
root@gigabyte:/var/log# v4l2ucp
X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    130 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x139
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 5 (X_ShmCreatePixmap)
  Resource id:  0x4a0000f
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x4a00010
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x4a00010
```

```
root@gigabyte:/var/log# guvcview
GUVCVIEW: version 2.0.5
GUVCVIEW: couldn't open /home/dave/.config/guvcview2/video0 for read: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: Inappropriate ioctl for device
V4L2_CORE: failed to subscribe events for control 0x0098090c: Invalid argument
V4L2_CORE: failed to subscribe events for control 0x00980910: Invalid argument
V4L2_CORE: failed to subscribe events for control 0x00980912: Invalid argument
V4L2_CORE: failed to subscribe events for control 0x00980914: Invalid argument
V4L2_CORE: failed to subscribe events for control 0x00980915: Invalid argument
V4L2_CORE: failed to subscribe events for control 0x00982000: Invalid argument
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
control[0]:(unknown - 0x6) 0x980001 'User Controls'
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
V4L2_CORE: V4L2_CAP_TIMEPERFRAME not supported
```

# Works OK - as in there is an image if blurry low resolution

```
root@gigabyte:/etc/modprobe.d# v4l2-ctl --list-devices
Camera (usb-0000:00:14.0-9):
/dev/video0
```

```
root@gigabyte:/etc/modprobe.d# v4l2-ctl -d /dev/video0 --list-ctrls

User Controls

                     brightness 0x00980900 (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                            hue 0x00980903 (int)    : min=1 max=127 step=1 default=64 value=64 flags=slider
                       exposure 0x00980911 (int)    : min=1 max=2372 step=1 default=700 value=597
                           gain 0x00980913 (int)    : min=0 max=255 step=1 default=63 value=63
```

# So V4L seems to be happy enough

```
Jul 11 12:00:32 gigabyte cheese[6092]: cheese-application.vala:211: Error during camera setup: No device found
Jul 11 12:00:32 gigabyte cheese[6092]: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed
```

# Skype version

```
dave@gigabyte:~$ cat /usr/share/skypeforlinux/version
v2.0.8
```

# The resolution is very low

```
root@gigabyte:~# v4l2-ctl --list-formats-ext
ioctl: VIDIOC_ENUM_FMT
Index       : 0
Type        : Video Capture
Pixel Format: 'S561' (compressed)
Name        : GSPCA SPCA561
Size: Discrete 320x240
Size: Discrete 352x288

Index       : 1
Type        : Video Capture
Pixel Format: 'GBRG'
Name        : 8-bit Bayer GBGB/RGRG
Size: Discrete 160x120
Size: Discrete 176x144

```

# Any other data that lsusb will dump...

```
root@gigabyte:~# lsusb -s 001:004 -v

Bus 001 Device 004: ID 046d:0929 Logitech, Inc. Labtec Webcam Pro
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0929 Labtec Webcam Pro
  bcdDevice            0.00
  iManufacturer           1        
  iProduct                2 Camera
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          233
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0370  1x 880 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0220  1x 544 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       9
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0290  1x 656 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      10
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x02c0  1x 704 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      11
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0360  1x 864 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      12
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03c0  1x 960 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      13
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x034d  1x 845 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)
```

---

