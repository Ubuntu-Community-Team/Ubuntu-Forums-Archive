---
title: "USB Endoscope Camera"
date: 2014-12-26
forum: Hardware
---

### Post by brilliantcontract on 2014-12-26
I use Ubuntu 14.10 64-bit OS
 

 USB Endoscope Camera Specification: [http://i.imgur.com/WN5j9hV.jpg](http://i.imgur.com/WN5j9hV.jpg)
 

 ```
dima@lol:~$ ls /dev/video* 

 /dev/video0  /dev/video1

``` 

 ```
dima@lol:~$ lsusb 

 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 004: ID 13d3:5165 IMC Networks  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 003 Device 002: ID 058f:5608 Alcor Micro Corp.  

 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 

 ```
dima@lol:~$ lsusb -vd 058f:5608

 Bus 003 Device 002: ID 058f:5608 Alcor Micro Corp.  
 Device Descriptor: 
   bLength                18 
   bDescriptorType         1 
   bcdUSB               2.00 
   bDeviceClass          239 Miscellaneous Device 
   bDeviceSubClass         2 ? 
   bDeviceProtocol         1 Interface Association 
   bMaxPacketSize0        64 
   idVendor           0x058f Alcor Micro Corp. 
   idProduct          0x5608  
   bcdDevice            0.03 
   iManufacturer           3  
   iProduct                1  
   iSerial                 0  
   bNumConfigurations      1 
   Configuration Descriptor: 
     bLength                 9 
     bDescriptorType         2 
     wTotalLength          407 
     bNumInterfaces          2 
     bConfigurationValue     1 
     iConfiguration          0  
     bmAttributes         0x80 
       (Bus Powered) 
     MaxPower              200mA 
     Interface Association: 
       bLength                 8 
       bDescriptorType        11 
       bFirstInterface         0 
       bInterfaceCount         2 
       bFunctionClass         14 Video 
       bFunctionSubClass       3 Video Interface Collection 
       bFunctionProtocol       0  
       iFunction               1  
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        0 
       bAlternateSetting       0 
       bNumEndpoints           1 
       bInterfaceClass        14 Video 
       bInterfaceSubClass      1 Video Control 
       bInterfaceProtocol      0  
       iInterface              1  
       VideoControl Interface Descriptor: 
         bLength                13 
         bDescriptorType        36 
         bDescriptorSubtype      1 (HEADER) 
         bcdUVC               1.00 
         wTotalLength           85 
         dwClockFrequency       30.000000MHz 
         bInCollection           1 
         baInterfaceNr( 0)       1 
       VideoControl Interface Descriptor: 
         bLength                18 
         bDescriptorType        36 
         bDescriptorSubtype      2 (INPUT_TERMINAL) 
         bTerminalID             1 
         wTerminalType      0x0201 Camera Sensor 
         bAssocTerminal          0 
         iTerminal               0  
         wObjectiveFocalLengthMin      0 
         wObjectiveFocalLengthMax      0 
         wOcularFocalLength            0 
         bControlSize                  3 
         bmControls           0x00000000 
       VideoControl Interface Descriptor: 
         bLength                 9 
         bDescriptorType        36 
         bDescriptorSubtype      3 (OUTPUT_TERMINAL) 
         bTerminalID             3 
         wTerminalType      0x0101 USB Streaming 
         bAssocTerminal          0 
         bSourceID               6 
         iTerminal               0  
       VideoControl Interface Descriptor: 
         bLength                 7 
         bDescriptorType        36 
         bDescriptorSubtype      4 (SELECTOR_UNIT) 
         bUnitID                 4 
         bNrInPins               1 
         baSource( 0)            1 
         iSelector               0  
       VideoControl Interface Descriptor: 
         bLength                11 
         bDescriptorType        36 
         bDescriptorSubtype      5 (PROCESSING_UNIT) 
       Warning: Descriptor too short 
         bUnitID                 5 
         bSourceID               4 
         wMaxMultiplier      32208 
         bControlSize            2 
         bmControls     0x0000157f 
           Brightness 
           Contrast 
           Hue 
           Saturation 
           Sharpness 
           Gamma 
           White Balance Temperature 
           Backlight Compensation 
           Power Line Frequency 
           White Balance Temperature, Auto 
         iProcessing             0  
         bmVideoStandards     0x1b 
           None 
           NTSC - 525/60 
           SECAM - 625/50 
           NTSC - 625/50 
       VideoControl Interface Descriptor: 
         bLength                27 
         bDescriptorType        36 
         bDescriptorSubtype      6 (EXTENSION_UNIT) 
         bUnitID                 6 
         guidExtensionCode         {564c97a7-7ea7-904b-8cbf-1c71ec303000} 
         bNumControl            16 
         bNrPins                 1 
         baSourceID( 0)          5 
         bControlSize            2 
         bmControls( 0)       0xff 
         bmControls( 1)       0xff 
         iExtension              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x82  EP 2 IN 
         bmAttributes            3 
           Transfer Type            Interrupt 
           Synch Type               None 
           Usage Type               Data 
         wMaxPacketSize     0x0010  1x 16 bytes 
         bInterval              15 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        1 
       bAlternateSetting       0 
       bNumEndpoints           0 
       bInterfaceClass        14 Video 
       bInterfaceSubClass      2 Video Streaming 
       bInterfaceProtocol      0  
       iInterface              0  
       VideoStreaming Interface Descriptor: 
         bLength                            14 
         bDescriptorType                    36 
         bDescriptorSubtype                  1 (INPUT_HEADER) 
         bNumFormats                         1 
         wTotalLength                      227 
         bEndPointAddress                  129 
         bmInfo                              0 
         bTerminalLink                       3 
         bStillCaptureMethod                 2 
         bTriggerSupport                     0 
         bTriggerUsage                       0 
         bControlSize                        1 
         bmaControls( 0)                    27 
       VideoStreaming Interface Descriptor: 
         bLength                            27 
         bDescriptorType                    36 
         bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED) 
         bFormatIndex                        1 
         bNumFrameDescriptors                5 
         guidFormat                            {59555932-0000-1000-8000-00aa00389b71} 
         bBitsPerPixel                      16 
         bDefaultFrameIndex                  1 
         bAspectRatioX                       0 
         bAspectRatioY                       0 
         bmInterlaceFlags                 0x00 
           Interlaced stream or variable: No 
           Fields per frame: 2 fields 
           Field 1 first: No 
           Field pattern: Field 1 only 
           bCopyProtect                      0 
       VideoStreaming Interface Descriptor: 
         bLength                            34 
         bDescriptorType                    36 
         bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED) 
         bFrameIndex                         1 
         bmCapabilities                   0x00 
           Still image unsupported 
         wWidth                            640 
         wHeight                           480 
         dwMinBitRate                 73728000 
         dwMaxBitRate                147456000 
         dwMaxVideoFrameBufferSize      614400 
         dwDefaultFrameInterval         333332 
         bFrameIntervalType                  2 
         dwFrameInterval( 0)            333332 
         dwFrameInterval( 1)            666666 
       VideoStreaming Interface Descriptor: 
         bLength                            34 
         bDescriptorType                    36 
         bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED) 
         bFrameIndex                         2 
         bmCapabilities                   0x00 
           Still image unsupported 
         wWidth                            320 
         wHeight                           240 
         dwMinBitRate                 18432000 
         dwMaxBitRate                 36864000 
         dwMaxVideoFrameBufferSize      153600 
         dwDefaultFrameInterval         333332 
         bFrameIntervalType                  2 
         dwFrameInterval( 0)            333332 
         dwFrameInterval( 1)            666666 
       VideoStreaming Interface Descriptor: 
         bLength                            34 
         bDescriptorType                    36 
         bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED) 
         bFrameIndex                         3 
         bmCapabilities                   0x00 
           Still image unsupported 
         wWidth                            160 
         wHeight                           120 
         dwMinBitRate                  4608000 
         dwMaxBitRate                  9216000 
         dwMaxVideoFrameBufferSize       38400 
         dwDefaultFrameInterval         333332 
         bFrameIntervalType                  2 
         dwFrameInterval( 0)            333332 
         dwFrameInterval( 1)            666666 
       VideoStreaming Interface Descriptor: 
         bLength                            34 
         bDescriptorType                    36 
         bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED) 
         bFrameIndex                         4 
         bmCapabilities                   0x00 
           Still image unsupported 
         wWidth                            352 
         wHeight                           288 
         dwMinBitRate                 24330240 
         dwMaxBitRate                 48660480 
         dwMaxVideoFrameBufferSize      202752 
         dwDefaultFrameInterval         333332 
         bFrameIntervalType                  2 
         dwFrameInterval( 0)            333332 
         dwFrameInterval( 1)            666666 
       VideoStreaming Interface Descriptor: 
         bLength                            34 
         bDescriptorType                    36 
         bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED) 
         bFrameIndex                         5 
         bmCapabilities                   0x00 
           Still image unsupported 
         wWidth                            176 
         wHeight                           144 
         dwMinBitRate                  6082560 
         dwMaxBitRate                 12165120 
         dwMaxVideoFrameBufferSize       50688 
         dwDefaultFrameInterval         333332 
         bFrameIntervalType                  2 
         dwFrameInterval( 0)            333332 
         dwFrameInterval( 1)            666666 
       VideoStreaming Interface Descriptor: 
         bLength                            10 
         bDescriptorType                    36 
         bDescriptorSubtype                  3 (STILL_IMAGE_FRAME) 
         bEndpointAddress                    0 
         bNumImageSizePatterns               1 
         wWidth( 0)                        640 
         wHeight( 0)                       480 
         bNumCompressionPatterns             1 
       VideoStreaming Interface Descriptor: 
         bLength                             6 
         bDescriptorType                    36 
         bDescriptorSubtype                 13 (COLORFORMAT) 
         bColorPrimaries                     1 (BT.709,sRGB) 
         bTransferCharacteristics            1 (BT.709) 
         bMatrixCoefficients                 4 (SMPTE 170M (BT.601)) 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        1 
       bAlternateSetting       1 
       bNumEndpoints           1 
       bInterfaceClass        14 Video 
       bInterfaceSubClass      2 Video Streaming 
       bInterfaceProtocol      0  
       iInterface              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x81  EP 1 IN 
         bmAttributes            5 
           Transfer Type            Isochronous 
           Synch Type               Asynchronous 
           Usage Type               Data 
         wMaxPacketSize     0x1400  3x 1024 bytes 
         bInterval               1 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        1 
       bAlternateSetting       2 
       bNumEndpoints           1 
       bInterfaceClass        14 Video 
       bInterfaceSubClass      2 Video Streaming 
       bInterfaceProtocol      0  
       iInterface              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x81  EP 1 IN 
         bmAttributes            5 
           Transfer Type            Isochronous 
           Synch Type               Asynchronous 
           Usage Type               Data 
         wMaxPacketSize     0x1400  3x 1024 bytes 
         bInterval               1 
     Interface Descriptor: 
       bLength                 9 
       bDescriptorType         4 
       bInterfaceNumber        1 
       bAlternateSetting       3 
       bNumEndpoints           1 
       bInterfaceClass        14 Video 
       bInterfaceSubClass      2 Video Streaming 
       bInterfaceProtocol      0  
       iInterface              0  
       Endpoint Descriptor: 
         bLength                 7 
         bDescriptorType         5 
         bEndpointAddress     0x81  EP 1 IN 
         bmAttributes            5 
           Transfer Type            Isochronous 
           Synch Type               Asynchronous 
           Usage Type               Data 
         wMaxPacketSize     0x1400  3x 1024 bytes 
         bInterval               1

``` 

 When I open cheese and choose /dev/video1 - I get just black screen, no errors, no any messages. /dev/video0 - work fine, it's my laptop web camera.
 

 In Windows 7 this endscope camera become work without installation any drivers or codecs.
 

 How to fix this thing? Help me please.

---

### Post by brilliantcontract on 2014-12-26
I try open /dev/video1 with mplayer, vcl and avconv (ffmpeg) as video stream - no results, just black screen (in mplayer green screen).

---

### Post by coldraven on 2014-12-26
Try installing uvcview
```
sudo apt-get install uvcview
```

Run uvcview in a terminal and then uncheck "Auto levels" and adjust the brightness.
Hopefully you will then see something. Then quit uvcview (there is no need to save) and try again with Cheese

---

### Post by flaymond on 2014-12-26
> Try installing uvcview
     Code:
     sudo apt-get install uvcview 
Run uvcview in a terminal and then uncheck "Auto levels" and adjust the brightness.
Hopefully you will then see something. Then quit uvcview (there is no need to save) and try again with Cheese

1+

Yes, try that...run

```
 cheese /dev/video1
```

It working good on Xubuntu

---

### Post by brilliantcontract on 2014-12-26
In guvcview turn off checkbox "White Balance Temperature, Auto" and manual adjusting didn't get any results - just black screen. But I get some errors in terminal while I adjusting endscope in guvcview.


Output messages guvcview for laptop webcam:
```

dima@lol:~$ guvcview -d /dev/video0
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 1
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0
Init. USB Camera (location: usb-0000:00:1a.0-1.2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30,
vid:13d3 
pid:5165 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/30
drawing controls

fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
write /home/dima/.config/guvcview/video0 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK

```


Output messages guvcview for endscope camera:
```

dima@lol:~$ guvcview -d /dev/video1
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video1 
Init. USB 2.0 Camera (location: usb-0000:00:14.0-1)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
vid:058f 
pid:5608 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls

fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
[B] Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
[B] Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
write /home/dima/.config/guvcview/video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK

```


I will try checkout this camera from some other live CD linux distributors and wrote results on this forum.

---

### Post by coldraven on 2014-12-26
> In guvcview turn off checkbox "White Balance Temperature, Auto" and manual adjusting didn't get any results - just black screen.
I was thinking that the "Auto level" would be for the Brightness and not the White Balance Temperature. Was that an option?

---

### Post by brilliantcontract on 2014-12-26
Auto... option is highlighted:

[IMG]http://oi57.tinypic.com/aytm9.jpg[/IMG]

---

### Post by coldraven on 2014-12-27
Sorry but I have run out of ideas :(
Hopefully someone else will know how to fix it.

---

### Post by phoenix137 on 2015-02-05
I am having a similar issue with a similar device. When I start up guvcview in a terminal, I get a little different sequence of messages:

```
write /home/wjason/.config/guvcview/video0 OKfree controls
cleaned allocations - 100%
Closing portaudio ...OK
Restarting: guvcview -d /dev/video1
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video1 
Init. USB 2.0 PC Camera (location: usb-0000:00:12.0-2.4.2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/5, 
vid:058f 
pid:5608 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/5
drawing controls


libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device
fps is set to 1/5
Checking video mode 320x240@32bpp : OK 
libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device
libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device



```

The differences between your messages and mine that strike me are while yours says:

```

...
vid:058f 
pid:5608 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls

fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
[B]Could not grab image (select timeout): Resource temporarily unavailable
[/B]
```

mine says:

```

...
vid:058f 
pid:5608 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/5
drawing controls
libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device
libv4l2: error turning on stream: No space left on device
VIDIOC_STREAMON - Unable to start capture: No space left on device

```

None of my disk partitions are close to full.

I am running 14.04 x64:

```
wjason@Tesla-SSD:~$ uname -a
Linux Tesla-SSD 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



```

here is my devcie info:

```
wjason@Tesla-SSD:~$ lsusb -vd 058f:5608


Bus 003 Device 033: ID 058f:5608 Alcor Micro Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x5608 
  bcdDevice            0.03
  iManufacturer           3 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          257
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               1 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              1 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           85
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00000000
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               6
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      4 (SELECTOR_UNIT)
        bUnitID                 4
        bNrInPins               1
        baSource( 0)            1
        iSelector               0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 5
        bSourceID               4
        wMaxMultiplier      32208
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x1b
          None
          NTSC - 525/60
          SECAM - 625/50
          NTSC - 625/50
      VideoControl Interface Descriptor:
        bLength                27
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 6
        guidExtensionCode         {564c97a7-7ea7-904b-8cbf-1c71ec303000}
        bNumControl            16
        bNrPins                 1
        baSourceID( 0)          5
        bControlSize            2
        bmControls( 0)       0xff
        bmControls( 1)       0xff
        iExtension              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              15
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         1
        wTotalLength                       77
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 0
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                1
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                  6144000
        dwMaxBitRate                  6144000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval        2000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           2000000
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
wjason@Tesla-SSD:~$

```


> **brilliantcontract said:**
> In guvcview turn off checkbox "White Balance Temperature, Auto" and manual adjusting didn't get any results - just black screen. But I get some errors in terminal while I adjusting endscope in guvcview.

...

Output messages guvcview for endscope camera:
```

dima@lol:~$ guvcview -d /dev/video1
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video1 
Init. USB 2.0 Camera (location: usb-0000:00:14.0-1)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
vid:058f 
pid:5608 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls

fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
[B]Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
[B]Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable[/B]
write /home/dima/.config/guvcview/video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK

```
...


---

### Post by phoenix137 on 2015-02-05
I should perhaps add that none of my partitions are close to full.

---

### Post by phoenix137 on 2015-02-05
SUCCESS!!  I looked up the error msg for v4l 'no space left on device' and learned it was really saying that the bandwidth of the USB had been used up.  I plugged the endoscope directly into my computer and got an image!

---

### Post by brilliantcontract on 2015-02-05
I plugged the endscope directly into my pc, but error still apper.
For using the endscope I run VirtualBox with WindowsXP and get stream from there.

---

