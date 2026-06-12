---
title: "Webcam Logitech QuickCam Pro 9000 not working in 14.04"
date: 2014-07-13
forum: Hardware
---

### Post by Zsolt_Tari on 2014-07-13
I have just upgraded my 12.04 64 bit server to 14.04 and the Webcam Logitech QuickCam Pro 9000 is no longer working with this new release but it worked perfectly in 12.04.
[COLOR=#ff0000]**UPDATE: working with motion      (all i did was:  **   [FONT=Arial][SIZE=2][FONT=Arial][SIZE=1][FONT=Arial][SIZE=3]***sudo apt-get install motion)***[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/COLOR]


 sudo uvcdynctrl -l
Listing available devices:
  video0   **UVC Camera (046d:0990)**
    Media controller device /dev/media0 doesn't exist
ERROR: Unable to list device entities: Invalid device or device cannot be opened. (Code: 5)

$ uname -a
Linux server 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


dmesg


 [ 2464.136262] usb 5-1: new full-speed USB device number 3 using uhci_hcd
[ 2464.309450] usb 5-1: New USB device found, idVendor=0403, idProduct=6001
[ 2464.309462] usb 5-1: New USB device strings: Mfr=0, Product=0, SerialNumber=3
[ 2464.309470] usb 5-1: SerialNumber: Reader 785D9E2
[ 2464.314552] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[ 2464.314657] usb 5-1: Detected FT232BM
[ 2464.314665] usb 5-1: Number of endpoints 2
[ 2464.314672] usb 5-1: Endpoint 1 MaxPacketSize 64
[ 2464.314679] usb 5-1: Endpoint 2 MaxPacketSize 64
[ 2464.314686] usb 5-1: Setting MaxPacketSize 64
[ 2464.315329] ftdi_sio ttyUSB0: Unable to read latency timer: -32
[ 2464.316531] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2478.088274] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2478.088445] ftdi_sio 5-1:1.0: device disconnected
[ 4692.207636] usb 2-2: USB disconnect, device number 10
[ 4703.232167] usb 2-2: new high-speed USB device number 12 using ehci-pci
[ 4703.491501] usb 2-2: New USB device found, idVendor=046d, idProduct=0990
[ 4703.491513] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[ 4703.491521] usb 2-2: SerialNumber: 532520EA
[ 4703.492153] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[ 4703.523393] input: **UVC Camera (046d:0990)** as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input16
[ 4703.907461] usb_audio: Warning! Unlikely big volume range (=3072), cval->res is probably wrong.
[ 4703.907473] usb_audio: [5] FU [Mic Capture Volume] ch = 1, val = 4608/7680/1

 lsusb
Bus 002 Device 005: ID 0dc4:0233 Macpower Peripherals, Ltd
Bus 002 Device 012: ID **046d:0990 Logitech, Inc. QuickCam Pro 9000**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


 sudo v4l2-ctl --all
Driver Info (not using libv4l2):
        Driver name   : uvcvideo
        Card type     : UVC Camera (046d:0990)
        Bus info      : usb-0000:00:1d.7-2
        Driver version: 3.13.9
        Capabilities  : 0x84000001
                Video Capture
                Streaming
                Device Capabilities
        Device Caps   : 0x04000001
                Video Capture
                Streaming
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
        Width/Height  : 320/240
        Pixel Format  : 'MJPG'
        Field         : None
        Bytes per Line: 0
        Size Image    : 102400
        Colorspace    : SRGB
Crop Capability Video Capture:
        Bounds      : Left 0, Top 0, Width 320, Height 240
        Default     : Left 0, Top 0, Width 320, Height 240
        Pixel Aspect: 1/1
Streaming Parameters Video Capture:
        Capabilities     : timeperframe
        Frames per second: 15.000 (15/1)
        Read buffers     : 0
                     brightness (int)    : min=0 max=255 step=1 default=128 value=128
                       contrast (int)    : min=0 max=255 step=1 default=32 value=32
                     saturation (int)    : min=0 max=255 step=1 default=32 value=32
 white_balance_temperature_auto (bool)   : default=1 value=1
                           gain (int)    : min=0 max=255 step=1 default=0 value=0
           power_line_frequency (menu)   : min=0 max=2 default=2 value=2
      white_balance_temperature (int)    : min=0 max=10000 step=10 default=4000 value=4000 flags=inactive
                      sharpness (int)    : min=0 max=255 step=1 default=224 value=224
         backlight_compensation (int)    : min=0 max=2 step=1 default=1 value=1
                  exposure_auto (menu)   : min=0 max=3 default=3 value=3
              exposure_absolute (int)    : min=1 max=10000 step=1 default=166 value=166 flags=inactive
         exposure_auto_priority (bool)   : default=0 value=1
                          focus (int)    : min=0 max=255 step=1 default=0 value=0
                      led1_mode (menu)   : min=0 max=3 default=3 value=3
                 led1_frequency (int)    : min=0 max=255 step=1 default=0 value=0
       disable_video_processing (bool)   : default=0 value=0
             raw_bits_per_pixel (int)    : min=0 max=1 step=1 default=0 value=0

---

