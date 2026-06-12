---
title: "Webcam somewhat works on Dell 1520"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by dreikin on 2008-02-10
To put it simply:
Dell 1520 built-in webcam,
Works via skype, 
But not camorama.

Any ideas?

(I've searched forums, but didn't SEEM to find anything to help, but I'm sick, so I could be mistaken)

---

### Post by dreikin on 2008-02-10
lsusb:
```
Bus 007 Device 002: ID 04a9:170c Canon, Inc. 
Bus 007 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 007 Device 005: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
```

v4l-info:
```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "Laptop Integrated Webcam"
        bus_info                : "0000:00:1d.7"
        version                 : 0.1.0
        capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "Camera 1"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "MJPEG"
        pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
        index                   : 1
        type                    : VIDEO_CAPTURE
        flags                   : 0
        description             : "YUV 4:2:2 (YUYV)"
        pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x56595559 [YUYV]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 640
        fmt.pix.sizeimage       : 153600
        fmt.pix.colorspace      : SRGB
        fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
        id                      : 9963776
        type                    : INTEGER
        name                    : "Brightness"
        minimum                 : 0
        maximum                 : 200
        step                    : 1
        default_value           : 90
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
        id                      : 9963777
        type                    : INTEGER
        name                    : "Contrast"
        minimum                 : 5
        maximum                 : 50
        step                    : 1
        default_value           : 30
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
        id                      : 9963778
        type                    : INTEGER
        name                    : "Saturation"
        minimum                 : 0
        maximum                 : 100
        step                    : 1
        default_value           : 64
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
        id                      : 9963779
        type                    : INTEGER
        name                    : "Hue"
        minimum                 : 0
        maximum                 : 255
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
        id                      : 134217728
        type                    : INTEGER
        name                    : "Backlight Compensation"
        minimum                 : 0
        maximum                 : 3
        step                    : 1
        default_value           : 3
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
        id                      : 134217729
        type                    : MENU
        name                    : "Power Line Frequency"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 2
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
        id                      : 134217730
        type                    : INTEGER
        name                    : "Sharpness"
        minimum                 : 0
        maximum                 : 31
        step                    : 1
        default_value           : 1
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+12)
        id                      : 134217740
        type                    : BOOLEAN
        name                    : "White Balance Temperature, Auto"
        minimum                 : 0
        maximum                 : 0
        step                    : 0
        default_value           : 1
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+13)
        id                      : 134217741
        type                    : INTEGER
        name                    : "White Balance Temperature"
        minimum                 : 2800
        maximum                 : 6500
        step                    : 1
        default_value           : 4527
        flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "Laptop Integrated Webcam"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 1600
        maxheight               : 1200
        minwidth                : 48
        minheight               : 32

channels
ioctl VIDIOCGCHAN: Invalid argument

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 29491
        hue                     : 0
        colour                  : 41942
        contrast                : 36408
        whiteness               : 21845
        depth                   : 16
        palette                 : YUYV

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 0

```

---

### Post by linux23dragon on 2008-02-10
> **dreikin said:**
> To put it simply:
Dell 1520 built-in webcam,
Works via skype, 
But not camorama.

Any ideas?

(I've searched forums, but didn't SEEM to find anything to help, but I'm sick, so I could be mistaken)

Hi dreikin

Your Webcam driver only supports V4L2 and camorama only supports V4L1.

---

### Post by dreikin on 2008-02-10
Ah, ok.  So what works with v4l2?  I've tried xsane and gqcam, but:

xsane:
```
Failed to open device `v4l:dev/video0': Invalid argument.
```

gqcam:
```
Segmentation fault (core dumped)
```

---

