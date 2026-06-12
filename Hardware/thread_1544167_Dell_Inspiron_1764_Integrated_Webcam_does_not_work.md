---
title: "Dell Inspiron 1764 Integrated Webcam does not work under 10.04"
date: 2010-08-02
forum: Hardware
---

### Post by blecha on 2010-08-02
I am running the: 

2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

My machine id Dell Inspiron 1764 I3

I am not sure that my integrated webcam ever worked (I was using another laptop for Skyping). Presently it does not. I am quite surprised that I did not find any mention of the problem on this forum or when googling. 

On boot the camera is detected (why as a kb ?):

(II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
(**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_1.3M: always reports core events
(**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
(II) Laptop_Integrated_Webcam_1.3M: Found keys
(II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "inspiron"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "compose:menu"

The /dev/video0 is created
See also extract from /var/log/udev at the end of this message
running "gstreamer-properties" from terminal > video > test  I have

gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error dequeuing buf: Input/output error
libv4l2: error dequeuing buf: Input/output error
libv4l2: error dequeuing buf: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Failed trying to get video frames from device '/dev/video0'. [gstv4l2bufferpool.c(573): gst_v4l2_buffer_pool_dqbuf (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
The buffer type is not supported, or the index is out of bounds, or no buffers have been allocated yet, or the userptr or length are invalid. device /dev/video0]

tail -12 /var/log/Xorg.0.log
(II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event13)
(**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_1.3M: always reports core events
(**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event13"
(II) Laptop_Integrated_Webcam_1.3M: Found keys
(II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "inspiron"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "compose:menu"
(EE) Laptop_Integrated_Webcam_1.3M: Failed to reopen device after 10 attempts.


I have Similar problem with "Cheese"

(II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
(**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_1.3M: always reports core events
(**) Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
(II) Laptop_Integrated_Webcam_1.3M: Found keys
(II) Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "inspiron"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "compose:menu"
(EE) Laptop_Integrated_Webcam_1.3M: Failed to reopen device after 10 attempts.

After second attempt /dev/video0 is removed and /dev/video1 is created

I have no problem to use USB logitech Webcam:

(II) config/udev: Adding input device UVC Camera (046d:0990) (/dev/input/event7)
(**) UVC Camera (046d:0990): Applying InputClass "evdev keyboard catchall"
(**) UVC Camera (046d:0990): always reports core events
(**) UVC Camera (046d:0990): Device: "/dev/input/event7"
(II) UVC Camera (046d:0990): Found keys
(II) UVC Camera (046d:0990): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (046d:0990)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "inspiron"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "compose:menu

------------------------------
/var/log/udev indicates:

UDEV  [1280595525.489503] add      /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/001/003
DEVTYPE=usb_device
DRIVER=usb
PRODUCT=c45/641d/9a07
TYPE=239/2/1
BUSNUM=001
DEVNUM=003
SEQNUM=1270
ID_VENDOR=CN0FJT7K7248702H0BAM
ID_VENDOR_ENC=CN0FJT7K7248702H0BAM
ID_VENDOR_ID=0c45
ID_MODEL=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ENC=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ID=641d
ID_REVISION=9a07
ID_SERIAL=CN0FJT7K7248702H0BAM_Laptop_Integrated_Webcam_1.3M
ID_BUS=usb
ID_USB_INTERFACES=:0e0100:0e0200:
MAJOR=189
MINOR=2
DEVLINKS=/dev/char/189:2
...
KERNEL[1280595525.575840] add      /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
SUBSYSTEM=input
PRODUCT=3/c45/641d/9a07
NAME="Laptop_Integrated_Webcam_1.3M"
PHYS="usb-0000:00:1a.0-1.4/button"
EV==3
KEY==100000 0 0 0 0 0 0
MODALIAS=input:b0003v0C45p641De9A07-e0,1,kD4,ramlsfw
SEQNUM=1570
...
UDEV  [1280595525.630124] add      /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7/event7 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7/event7
SUBSYSTEM=input
DEVNAME=/dev/input/event7
SEQNUM=1571
ID_INPUT=1
ID_INPUT_KEY=1
ID_VENDOR=CN0FJT7K7248702H0BAM
ID_VENDOR_ENC=CN0FJT7K7248702H0BAM
ID_VENDOR_ID=0c45
ID_MODEL=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ENC=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ID=641d
ID_REVISION=9a07
ID_SERIAL=CN0FJT7K7248702H0BAM_Laptop_Integrated_Webcam_1.3M
ID_TYPE=video
ID_BUS=usb
ID_USB_INTERFACES=:0e0100:0e0200:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=uvcvideo
ID_PATH=pci-0000:00:1a.0-usb-0:1.4:1.0
XKBMODEL=inspiron
XKBLAYOUT=us
MAJOR=13
MINOR=71
DEVLINKS=/dev/char/13:71 /dev/input/by-id/usb-CN0FJT7K7248702H0BAM_Laptop_Integrated_Webcam_1.3M-event-if00 /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-event
XKBOPTIONS=compose:menu
UDEV  [1280595525.632187] add      /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/video4linux/video0 (video4linux)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/video4linux/video0
SUBSYSTEM=video4linux
DEVNAME=/dev/video0
SEQNUM=1569
ID_V4L_VERSION=2
ID_V4L_PRODUCT=Laptop_Integrated_Webcam_1.3M
ID_V4L_CAPABILITIES=:capture:
ID_VENDOR=CN0FJT7K7248702H0BAM
ID_VENDOR_ENC=CN0FJT7K7248702H0BAM
ID_VENDOR_ID=0c45
ID_MODEL=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ENC=Laptop_Integrated_Webcam_1.3M
ID_MODEL_ID=641d
ID_REVISION=9a07
ID_SERIAL=CN0FJT7K7248702H0BAM_Laptop_Integrated_Webcam_1.3M
ID_TYPE=video
ID_BUS=usb
ID_USB_INTERFACES=:0e0100:0e0200:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=uvcvideo
ID_PATH=pci-0000:00:1a.0-usb-0:1.4:1.0
ACL_MANAGE=1
MAJOR=81
MINOR=0
DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-CN0FJT7K7248702H0BAM_Laptop_Integrated_Webcam_1.3M-video-index0 /dev/v4l/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-video-index0

---

