---
title: "Integrated WEBcam FJS Amilo Si2636"
date: 2008-04-26
forum: Hardware
---

### Post by nukleuzN on 2008-04-26
Hi, im not sure if im posting in the correct forum - but; I have an FJS Amilo Si2636, with en integrated WebCam.. I dont get this to work with Ubuntu 8.04 LTS. Is there any way to get this to work?

:popcorn:

Pic, PC: [http://img.pte.at/photo_db/hi_res/hires30361.jpg](http://img.pte.at/photo_db/hi_res/hires30361.jpg)
Pic, screendump using "Cheese": [[img]http://bildr.no/thumb/190643.jpeg[/img]](http://bildr.no/view/190643)

---

### Post by linuxwizard on 2008-04-26
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga didn't work post results of the command > lsusb

---

### Post by nukleuzN on 2008-04-26
Hi, and thanks for your answer:)

Unfortunally, ekiga didnt work :( It says that my driver is'nt compatible. Tried the command in terminal, and here is the result:
```
Bus 007 Device 004: ID 5986:0202 Bison 
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```
It didnt tell me so mutch. Is there any other options?

---

### Post by linuxwizard on 2008-04-26
I don't see a webcam listed. Do you dualboot with M$ ? Does the webcam work there ?

---

### Post by nukleuzN on 2008-04-27
I dont have a dualboot, no. But when i got the machine for a week ago, Vista was installed. The cam worked... After i installed ubuntu, the cam wouldnt work anymore.

When i remove the lens-cover, the cam is activated. The cam is described as "USB2.0 cam" or "v412: USB2.0 Camera". 

I dont know how this "on-off" function work in the lens-cover, could this be the problem? When i was using Vista - the cam was disconnected if the cover was closed (coulnt find it in the driverlist, or use it in MSN).

EDIT:
```
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```tried the "lsusb" in terminal with the lens-cover closed. "Bison" on line1 is missing then, this is the result with the lens-cover open:```
Bus 007 Device 011: ID 5986:0202 Bison 
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
**lsusb -v -d 5986:0202:**
```
joachim@joachim-ubuntu:~$ lsusb -v -d 5986:0202

Bus 007 Device 011: ID 5986:0202 Bison 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x5986 Bison
  idProduct          0x0202 
  bcdDevice            0.02
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          704
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
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
        wTotalLength           84
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  2
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
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000053f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          Backlight Compensation
          Power Line Frequency
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
        wMaxPacketSize     0x0008  1x 8 bytes
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
        bLength                            15
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                        2
        wTotalLength                      557
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       1
        bControlSize                        1
        bmaControls( 0)                    11
        bmaControls( 1)                    11
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        1
        bNumFrameDescriptors                6
        bFlags                              1
          Fixed-size samples: Yes
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      921600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x01
          Still image supported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      230400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x01
          Still image supported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       57600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x01
          Still image supported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      304128
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x01
          Still image supported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       76032
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     3932160
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  2
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               6
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        320
        wHeight( 1)                       240
        wWidth( 2)                        160
        wHeight( 2)                       120
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        176
        wHeight( 4)                       144
        wWidth( 5)                       1280
        wHeight( 5)                      1024
        bNumCompressionPatterns             6
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        2
        bNumFrameDescriptors                6
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x01
          Still image supported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      230400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x01
          Still image supported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       57600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x01
          Still image supported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      304128
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x01
          Still image supported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       76032
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  3
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
        dwFrameInterval( 2)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     3932160
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1428571
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               6
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                        320
        wHeight( 1)                       240
        wWidth( 2)                        160
        wHeight( 2)                       120
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        176
        wHeight( 4)                       144
        wWidth( 5)                       1280
        wHeight( 5)                      1024
        bNumCompressionPatterns             6
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

---

### Post by nukleuzN on 2008-04-27
I have updated my posts with a litlebit more information about my hardware. Looking forward to get the cam working again ;)

---

### Post by linuxwizard on 2008-04-27
When I tried searching for Bison before I thought maybe that was your cam but it was not coming up as a webcam. I am going to do more searching in the mean time try this > open Ekiga > Edit > Preferences > Devices > Video Devices > try changing  Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L. Than see if cam will work.

---

### Post by nukleuzN on 2008-04-28
No - the same results. Det icon is just jumping up and down. Is there anything i can do with the driver? Or any other suggestions how i can fix this?

---

### Post by linuxwizard on 2008-04-28
Alot of webcams will just work no need to install a driver. But first you need to test your cam to see if it will work. Why install a driver if you don't need to. That is what I have been doing with you checking to see if cam will work. Now I can't find any listings of a driver or your webcam > Bus 007 Device 011: ID 5986:0202 Bison > you might try this driver > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > I have no idea if it will work I just think it is the best one to try.  Good Luck

---

### Post by heima on 2008-04-29
I've got the same problem. I posted a bug on the uvcvideo berlios project page:
[http://developer.berlios.de/bugs/?func=detailbug&bug_id=13691&group_id=5681](http://developer.berlios.de/bugs/?func=detailbug&bug_id=13691&group_id=5681)

I hope it's not my cam that is borked. It does not work in Vista either. I get a black picture just like nukleuzN.

---

### Post by nukleuzN on 2008-04-29
My cam works in Vista - are you sure you take the lenscover all the way back? It should be a click when its open and turned "on".

Havent found out about my problem - have tried all. Think I have installed the driver correctly:

 Compile Linux-UVC

   1. Enter the check-out Linux-UVC folder
      cd trunk
   2. Open the Make file in this directory
      sudo nano Makefile
   3. Edit Makefile to change the modules path from
      INSTALL_MOD_DIR := usb/media
      to
      INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo
   4. make
   5. sudo make install

Is the driver correctly installed now?

---

### Post by heima on 2008-04-30
You don't have to do a make install. I believe you can just insmod the resulting uvcvideo.ko file. If you remember to remove the "default" module first, I think that will be one way to do it without having to worry about conflicts yet.

Did you download any special drivers for Vista or did you use the one Vista provides? I am afraid that my camera is completely busted.

---

### Post by nukleuzN on 2008-05-01
Hmmmm what do you mean? Busted? It woulnt work?

Anyway - the driver is not a special one.

---

### Post by scananza on 2008-05-29
Hello,
I have the same laptop and experiencing the same issue.
I think this webcam is still unsupported, uvc driver reports that 5986:0200 is supposed to work but we got 5986:0202... too bad
I guess we have to wait some time.....
BTW if someone will tweak it for good, please post some howto :^D

p.s. a bug report has already been filed to developers:

[http://developer.berlios.de/bugs/?func=detailbug&bug_id=13691&group_id=5681]("http://developer.berlios.de/bugs/?func=detailbug&bug_id=13691&group_id=5681")

---

### Post by scananza on 2008-06-05
Hello,
I finally got the webcam working on the Amilo Si2636. :cool:

These are the steps I followed:

[LIST]download linux uvc driver from here, following the instructions reported on the site:

[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

[/LIST]
[LIST]edit Makefile and change:
```
INSTALL_MOD_DIR	:= ubuntu/media/usbvideo
```[/LIST]
[LIST]edit uvc_video.c and comment out:
```
/*if (ret != size) {
		uvc_printk(KERN_ERR, "Failed to query (%u) UVC control %u "
			"(unit %u) : %d (exp. %u).\n", query, cs, unit, ret,
			size);
		return -EIO;
}*/
```
This will simply bypass the check routine that fails on our laptop...[/LIST]
[LIST]make and sudo make install should install the new driver (it will overwrite standard ubuntu modules so you'll probably have harmless checksum errors when those packages will be removed/upgraded, but that can be easily workedaround)[/LIST]
[LIST]eventually rmmod uvcvideo and reattach the camera and it should work, at least it does for me![/LIST]

Please, if you can, confirm that's working for you too in order to help having this fixed in the next releases!

Bye and enjoy the cam! \\:D/

---

### Post by nukleuzN on 2008-06-08
Hi, thanx for your post!!

I have doin' this, but; how do i rmmod uvcvideo? 

```
root@joachim-ubuntu:/home/joachim# cd trunk/
root@joachim-ubuntu:/home/joachim/trunk# make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/joachim/trunk/uvc_driver.o
  CC [M]  /home/joachim/trunk/uvc_queue.o
  CC [M]  /home/joachim/trunk/uvc_v4l2.o
  CC [M]  /home/joachim/trunk/uvc_video.o
  CC [M]  /home/joachim/trunk/uvc_ctrl.o
  CC [M]  /home/joachim/trunk/uvc_status.o
  CC [M]  /home/joachim/trunk/uvc_isight.o
  LD [M]  /home/joachim/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/joachim/trunk/uvcvideo.mod.o
  LD [M]  /home/joachim/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
root@joachim-ubuntu:/home/joachim/trunk# make install
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  INSTALL /home/joachim/trunk/uvcvideo.ko
  DEPMOD  2.6.24-18-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
root@joachim-ubuntu:/home/joachim/trunk# nano /home/joachim/trunk/Makefile
root@joachim-ubuntu:/home/joachim/trunk# locate uvcvideo
/home/joachim/trunk/.uvcvideo.ko.cmd
/home/joachim/trunk/.uvcvideo.mod.o.cmd
/home/joachim/trunk/.uvcvideo.o.cmd
/home/joachim/trunk/uvcvideo.h
/home/joachim/trunk/uvcvideo.ko
/home/joachim/trunk/uvcvideo.mod.c
/home/joachim/trunk/uvcvideo.mod.o
/home/joachim/trunk/uvcvideo.o
/home/joachim/trunk/.svn/text-base/uvcvideo.h.svn-base
/home/joachim/trunk/.tmp_versions/uvcvideo.mod
/lib/modules/2.6.24-16-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.24-17-generic/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.24-18-generic/ubuntu/media/usbvideo/uvcvideo.ko
root@joachim-ubuntu:/home/joachim/trunk# 
```

These are the steps i have been taken... Haven't rmmod'ed the uvcvideo yet, since i dont know what uvcvideo i should rmmod ?? :/

Again, thanx for your help!

**_EDIT:_**
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
= rmmod on this:
/lib/modules/2.6.24-18-generic/ubuntu/media/usbvideo/uvcvideo.ko
[B][I]
The cam did work, but it was very "blurry". The picture is quite more clearer on Vista. How come? Is it because this is just a work around on a driver thats not compatible with this cam?[/I][/B]

---

### Post by scananza on 2008-06-09
Hello!

rmmod is only necessary if you have old module loaded into kernel, if not you can just modprobe the new driver...

you can eventually reboot your system and should get it working right away!

I don't seem to get blurry pictures even though I cannot compare with vista's since I blew it up on the very first run of the laptop :^D

is it something related to webcam management program maybe?

I only used it with cheese actually!

---

### Post by DarthCaedus on 2008-06-09
I'm using cheese, my cam is working, but the image is upside down!
My note is a Asus W7S, and besides hanging (sometimes) when I tried to turn the bluetooth mouse on
is doing great!

---

### Post by nukleuzN on 2008-06-09
Hmm, im not sure if i do understand all the steps.

I have tried to use the Cam, but it want work.
- Does that mean that i have an old module in my kernel?

Is this the correct guideline:

1. root@joachim-laptop:/home/joachim# svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

2. root@joachim-laptop:/home/joachim# cd trunk/

3. root@joachim-laptop:/home/joachim/trunk# nano Makeinstall
3.2 "INSTALL_MOD_DIR	:= ubuntu/media/usbvideo"

4. root@joachim-laptop:/home/joachim/trunk# nano uvc_video.c
4.2 Comment out lines you reffered to,

5. root@joachim-laptop:/home/joachim/trunk# make
6. root@joachim-laptop:/home/joachim/trunk# make install

7. root@joachim-laptop:/home/joachim/trunk# rmmod /lib/modules/2.6.24-18-generic/ubuntu/media/usbvideo/uvcvideo.ko

?? :S 

Im pretty new to Linux.

Thx for ur help!

EDIT:

Have no reinstalled Ubuntu 8.04, so my OS is clean. As i said earlier; my cam did work, but it was blurry. So i thougth a clean OS and a clear guideline will help me to a bedre quality. I have tried my cam without doing the steps above, after install.

---

### Post by scananza on 2008-06-10
Hi,
yes the steps you followed are correct, you don't need to give rmmod full module path since it loads from /lib/modules/* directly, just:

$ sudo rmmod uvcvideo
$ sudo modprobe uvcvideo

this should enable the correct driver...

for the blurriness don't really know what to tell you, maybe you should ask to the uvcvideo developers or file a bug report there!

---

### Post by nukleuzN on 2008-06-10
Hi and thx again,

Will try these steps after work. :)

I hope the reason for bad quality is because this is a work around of a driver that actually shouldn't work for this cam. I can paste som pictures from my external 1.3mpx cam that had the same quality as the integrated Si2636 had on Vista, and one picture of my Si2636 cam on linux.

Then you can se the difference. Maby you can compare your quality too, and give me a feedback on witch picture is approximate similar to yours.

---

### Post by nukleuzN on 2008-06-10
Here is the screen dumps. The external cam is one on the top. Linux below.
[B]
Is there a way to remove the driver completely and reinstall it?[/B]

EDIT: The "quickcam" driver made my day!! :D The quality of my Si2636 cam is no officially the same as the cam picture at the top ;) Bye bye "bottom picuture" =;


**[COLOR="Red"]If you need the driver - mail me[/COLOR]** :D

---

### Post by nukleuzN on 2008-06-11
Seems like it wouldnt work anymore after the restart. :/ Think i give up now, and wait for the uvc driver....

---

### Post by 64stefano64 on 2008-07-04
Hi all

followed all steps. but I have this result at the end:

stefano@stefano-linux:~$ cd trunk
stefano@stefano-linux:~/trunk$ rmmod /lib/modules/2.6.24-18-generic/ubuntu/media/usbvideo/uvcvideo.ko
ERROR: Module uvcvideo does not exist in /proc/modules
stefano@stefano-linux:~/trunk$ sudo rmmod uvcvideo
[sudo] password for stefano: 
ERROR: Module uvcvideo does not exist in /proc/modules
stefano@stefano-linux:~/trunk$ sudo rmodprobe uvcvideo
sudo: rmodprobe: command not found
stefano@stefano-linux:~/trunk$ sudo modprobe uvcvideo

can you help me?

Thanks Stefano

---

### Post by sripplinger on 2008-07-22
I also had the same result at the end:

scott@Johann:~/trunk$ sudo rmmod uvcvideo
ERROR: Module uvcvideo does not exist in /proc/modules

What gives?

---

### Post by heima on 2008-07-23
Have you tried (after switching on the cam) simply insmod'ing the built module?
e.g:
# insmod /path/to/my/driver/uvcvide.ko

---

### Post by nukleuzN on 2008-08-18
Any new information about an driver-update om similar?

---

### Post by ArnoraCom on 2008-10-18
Hi!

I am having this same problem with unusable integrated WebCam in Fujitsu-Siemens Si2636. Otherwise Ubuntu 8.04 Hardy Heron seems to work perfectly in this laptop. (OK, there are so oddities with the Intel 965 Graphic and video projector connected to HDMI...)

Does anyone know if Ubuntu 8.10 is going to include a working driver for the integrated Bison WebCam, or if there is work done to bring the support for Bison otherwise soon? Or should I try to fix it by hand?

Best Regards,
Jukka

---

### Post by heima on 2008-10-18
This is a temporary solution, guys:

[http://ubuntuforums.org/showpost.php?p=5247345&postcount=3](http://ubuntuforums.org/showpost.php?p=5247345&postcount=3)

Basically download the SVN version of the driver and uncomment the specified lines. Enjoy webcamming!:guitar:

(I'm actually using Mandriva these days)

---

### Post by kalleb on 2009-01-13
I don't know if anyone has tried this but I got my webcam on my  si2636 to work using this guide: [http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial)

Hopefully it will benefit someone.

/Cheers

---

### Post by heima on 2009-01-14
When using Fedora, the builtin driver works perfectly. Does the newest drivers in Ubuntu work as well now?

---

### Post by nukleuzN on 2009-01-25
> **kalleb said:**
> I don't know if anyone has tried this but I got my webcam on my  si2636 to work using this guide: [http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial)

Hopefully it will benefit someone.

/Cheers
Yeep! It does work now. Thx. 

But still... The QUALITY is not the same as with the original driver in VISTA :( 

**#¤%!$£+?** (bad words)

---

