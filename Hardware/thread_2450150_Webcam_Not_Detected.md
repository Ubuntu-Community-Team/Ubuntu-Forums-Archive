---
title: "Webcam Not Detected"
date: 2020-09-08
forum: Hardware
---

### Post by davehumphreys02186 on 2020-09-08
Hello all,

I have searched for a solved thread on this and could not find one. The integrated webcam on my Dell laptop does not work, this is what I get:

lsusb:

```
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

guvcview:

```
GUVCVIEW: version 2.0.6
V4L2_CORE: ERROR opening V4L interface: No such file or directory
GUVCVIEW (1): Guvcview error
     no video device found

(guvcview:7305): Gtk-WARNING **: 08:42:16.806: Theme parsing error: <data>:1:17: not a number

(guvcview:7305): Gtk-WARNING **: 08:42:16.806: Theme parsing error: <data>:1:31: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(guvcview:7305): Gtk-WARNING **: 08:42:16.806: Theme parsing error: <data>:1:17: not a number

(guvcview:7305): Gtk-WARNING **: 08:42:16.806: Theme parsing error: <data>:1:32: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
```

cheese:

```
** Message: 10:49:20.390: cheese-application.vala:214: Error during camera setup: No device found


(cheese:11140): cheese-CRITICAL **: 10:49:20.637: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:11140): GLib-CRITICAL **: 10:49:20.637: g_variant_new_string: assertion 'string != NULL' failed

(cheese:11140): GLib-CRITICAL **: 10:49:20.637: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:11140): GLib-GIO-CRITICAL **: 10:49:20.637: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:11140): GLib-CRITICAL **: 10:49:20.637: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:11140): GLib-GIO-CRITICAL **: 10:49:20.637: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:11140): GLib-CRITICAL **: 10:49:20.637: g_variant_unref: assertion 'value != NULL' failed

** (cheese:11140): CRITICAL **: 10:49:20.637: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed



```

when I plug a USB webcam, I get this:

```
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 008: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

cheese:

```
** Message: 10:50:50.609: cheese-application.vala:214: Error during camera setup: No device found


(cheese:11371): cheese-CRITICAL **: 10:50:50.649: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:11371): GLib-CRITICAL **: 10:50:50.649: g_variant_new_string: assertion 'string != NULL' failed

(cheese:11371): GLib-CRITICAL **: 10:50:50.649: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:11371): GLib-GIO-CRITICAL **: 10:50:50.649: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:11371): GLib-CRITICAL **: 10:50:50.649: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:11371): GLib-GIO-CRITICAL **: 10:50:50.649: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:11371): GLib-CRITICAL **: 10:50:50.649: g_variant_unref: assertion 'value != NULL' failed

** (cheese:11371): CRITICAL **: 10:50:50.649: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed


```

cuvcview goes nuts and crashes, this is all I can grab:

```
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
V4L2_CORE: (get_v4l2_frame) video stream must be started first
```


Any help would be greatly appreciated, thanks.

---

### Post by TheFu on 2020-09-08
How much is a solution worth to you?  $40 or more?  

I ask because there are well supported USB webcams that are known to "just work" with Ubuntu and Linux in general.  Guys in my LUG use Logitech C270 ($38) and Logitech C920 ($90-ish) webcams.  Wish I had a non-Logitech suggestion, because supporting a company that took a long time to support Linux bothers me, but those are the ones we've found that are no hassle, plug in and work devices across a wide range of Linux systems.

I did find a post here from 2008-2011 about that model of webcam. People jumped through all sorts of hoops and didn't get it working. I've had webcams die and never work again, but that was a very cheap IBM cam that was sitting in a window taking a photo outside every 30 seconds, 24/7/365 and posting to one of my websites.  I think the sensor failed from sun exposure. I replaced it with a cheap webcam that never worked, then finally bought a C920 which only worked on Windows until around 2016. I think google's success with chromebooks got Logitech to actively start supporting Linux.  One day, out of frustration, I just plugged it in and it worked.  Moved to a Linux system and it worked too. I was shocked.

---

### Post by davehumphreys02186 on 2020-09-08
Hello, thank you for the sage response -- I bought a Logitech for 44 bucks delivered by Thursday. Again, thank you...I am a civilian and not a tech person though I have been running Ubuntu since Hardy though I have not been in the forums for ages and ages. Did spend hours and hours on this webcam thing for the fun of it, but at some point it is not fun any more and time to bail out -- 44 bucks is money well spent, Cheers..

---

### Post by TheFu on 2020-09-08
You already have a "logitech", so I really hope you got one of the models recommended.  If it weren't for this pandemic, these things are usually about $10-$15 cheaper. Ah --- supply and demand.  Be certain to disable the onboard webcam and perhaps the onboard microphone in the BIOS before connecting the new USB device. It will make your life easier.

With both the C920 and C270 models, our group doesn't have any issues with using PC speakers - no headset or carefully input limited mic settings are usually needed.

The extra features that work in Windows, mainly logical zoom, work, but not in any interface I've seen in Linux.  Save these commands:
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200
$ v4l2-ctl -d /dev/video0 -c brightness=100
$ v4l2-ctl --list-devices
$ v4l2-ctl --list-formats
```

You may have use of them later.

The zoom of 200 is the max. Ranges from 50 - 200 seem to work.
For brightness, 100 is whatever the cam figures out. I've had it lower 1 value every minute on video chats where I really didn't want to stay too long. By 50, I'm in a dark room as far as the chat shows. ;) Because it is a subtle change, nobody notices it gradually change.

There are other settings that can be tweaked using the **v4l2-ctl** tool. The manpage lists them all. Perhaps there's some hidden settings in some advanced video tools like OBS, but who has time for that when I can script what I want?

---

### Post by davehumphreys02186 on 2020-09-08
So yes I bought a 270. The logitech in lsusb that I attempted to use is an old Express that came with a Gateway computer about 30 years ago (!) so I am not surprised that it didn't work, but what the hell you never know.

Thanks for the code and the tips and the time, I am sure this will all work out. Cheers.

---

### Post by davehumphreys02186 on 2020-09-08
[IMG]https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse2.mm.bing.net%2Fth%3Fid%3DOIP.lG-0BwemhxvUrb0bge8EiwAAAA%26pid%3DApi&f=1[/IMG]

---

### Post by davehumphreys02186 on 2020-09-29
Hello. It came, I plugged it in, it worked. Thanks.

---

