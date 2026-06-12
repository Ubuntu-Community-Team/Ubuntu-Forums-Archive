---
title: "Pavilion 9660eg - webcam problems"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by Neo¹ on 2007-12-09
Hi All,

I have an Laptop HP Pavilion 9660eg and I'm trying to get the integrated webcam to work.
The funny think is, that the webcam works correctly with Kopete. 
But I cannot use this webcam in any other program. 
When I type ~$ v4l-info I got this info:
```



### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "HP Webcam"
        bus_info                : "0000:00:02.1"
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
        minimum                 : -64
        maximum                 : 127
        step                    : 1
        default_value           : 30
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
        id                      : 9963777
        type                    : INTEGER
        name                    : "Contrast"
        minimum                 : 0
        maximum                 : 95
        step                    : 1
        default_value           : 26
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
        id                      : 9963778
        type                    : INTEGER
        name                    : "Saturation"
        minimum                 : 0
        maximum                 : 150
        step                    : 1
        default_value           : 138
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
        id                      : 9963779
        type                    : INTEGER
        name                    : "Hue"
        minimum                 : -40
        maximum                 : 40
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
        id                      : 134217728
        type                    : INTEGER
        name                    : "Backlight Compensation"
        minimum                 : 0
        maximum                 : 1
        step                    : 1
        default_value           : 0
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
        maximum                 : 200
        step                    : 1
        default_value           : 100
        flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "HP Webcam"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 640
        maxheight               : 480
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
        brightness              : 32253
        hue                     : 32768
        colour                  : 60292
        contrast                : 17936
        whiteness               : 39718
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

So it seems to be all ok but when I type ~$ v4l-conf I got this:
```
v4l-conf: using X11 display :1.0
WARNING: Your X-Server has no DGA support.
mode: 1440x900, depth=24, bpp=32, bpl=5760, base=unknown
/dev/video0 [v4l2]: no overlay support

```

I use compiz-fusion with XGL. Could it be the problem?

When I starting some program to grab the video from webcam I got this or similar errors:
```
 webcam
reading config file: /home/radek/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [16 bit YUV 4:2:2 (packed, YUYV)]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=AN                                                                                                                          Y;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecod                                                                                                                          e.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): In                                                                                                                          valid argument
capturing image failed

```

Has someone an idea what the problem could be?

Kind regards,
Neo

---

