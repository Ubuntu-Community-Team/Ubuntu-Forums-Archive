---
title: "USB Mic &amp; Webcam regurarily not working"
date: 2021-06-08
forum: Hardware
---

### Post by Matyy on 2021-06-08
Hi,

we have a few Intel NUCs set up with Ubuntu 20.04 as meeting room pcs, to use with Zoom, Teams, Webex & so on.

We use "Logitech BRIO 4k" webcams and "Jabbra SPEAK 410/510" table microphones/speakers.

And it's sadly a disaster.

The "apps" (websites) work fine in linux. But the webcams and the microphones regurarily just stop working. Than you need to plug them out and back in again, sometimes only a reboot helps. Strangely, the speaker keeps working, there is just no input from the microphone. The hardware is fine and works flawlessly in Windows.

They are rebooted every night, but won't even last a day.

I wonder, is it worth my time to try to fix these isues? Or is that just the state of things right now?

Thanx

mty

---

### Post by TheFu on 2021-06-08
If the USB connections are solid, they can become disconnected.  PulseAudio could be configured to automatically change the device used based on the last one plugged in.  That can be disabled by removing the _module-switch-on-connect_

To remove that module, use **pacmd unload-module module-switch-on-connect**
To add it back in, use **pacmd load-module module-switch-on-connect**

I can't help with the webcam. My logitech C920 just works.  The only time the system gets confused is when different microphones are connected/disconnected.  A default device can be set ... 
```
# Get a list of microphones:
$ pactl list short sources
# Set the default microphone
$ pacmd set-default-source alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo
```

If you need to set the default speaker/output, use 
```
# Get a list of output devices
$ pactl list short sinks
```

May want to monitor the room to keep non-Linux people from trying to "fix it" too.  Helpful people often are not.

---

### Post by him610 on 2021-06-11
> Logitech BRIO 4k webcams 
I thought about this overnight. Using a 4k camera would generate a lot of data (bits). Those bits need to go somewhere; maybe to buffers; I don't know. Is there someway to reduce the 4k down to something like 1024, or possibly increase buffer capacity. I don't know, just tossing out ideas as they come to mind.

Where are the subject matter experts when one needs them?

---

### Post by TheFu on 2021-06-11
[https://www.reddit.com/r/linux/comments/f2icry/psa_logitech_has_removed_hardware_h264_encoder/](https://www.reddit.com/r/linux/comments/f2icry/psa_logitech_has_removed_hardware_h264_encoder/)
says that some recent Logitech webcams removed the h.264 encoding hardware.  I know my C920 does have the h.264 encoding hardware.
```
$ v4l2-ctl --info --list-formats
Driver Info (not using libv4l2):
        Driver name   : uvcvideo
        Card type     : HD Pro Webcam C920
        Bus info      : usb-0000:01:00.0-3
        Driver version: 5.4.114
        Capabilities  : 0x84A00001
                Video Capture
                Metadata Capture
                Streaming
                Extended Pix Format
                Device Capabilities
        Device Caps   : 0x04200001
                Video Capture
                Streaming
                Extended Pix Format
ioctl: VIDIOC_ENUM_FMT
        Index       : 0
        Type        : Video Capture
        Pixel Format: 'YUYV'
        Name        : YUYV 4:2:2

        Index       : 1
        Type        : Video Capture
        Pixel Format: **'H264' (compressed)**
        Name        : H.264

        Index       : 2
        Type        : Video Capture
        Pixel Format: 'MJPG' (compressed)
        Name        : Motion-JPEG
```
In software, it is possible to control the pixel resolution.  I don't know the exact command, often the GUI used will have a method to control that.
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200
$ v4l2-ctl -d /dev/video0 -c brightness=100
``` are some other commands that I know work. Just need to ensure the video device is properly specified.  There is a way, using udev, to force a camera to have a specific device name - say, /dev/video9.  Then we can more easily script stuff. I only have 1 webcam, so as long as I don't start a virtual video source before connecting the webcam, then the device names are the same.

As for bandwidth needs, I'd be more worried about people trying to use wifi connections than the WAN bandwidth at a company. Wifi bandwidth is very difficult to control, especially in places where 20-200 wifi devices might be using the same AP.  Never believe the reported connection speed. Those are lies.  Only actual transmitted data, when the environment is exactly the same as during a meeting, can let you know what the real speed is.  If there are 5 people in the room using their phones and/or laptops too, then that needs to be part of the bandwidth testing.  Much easier to wire up the video conferencing equipment and avoid wifi completely.

---

