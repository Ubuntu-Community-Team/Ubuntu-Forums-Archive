---
title: "cheese do not connect to webcam"
date: 2016-01-31
forum: Hardware
---

### Post by francois_baret on 2016-01-31
When plugged the Aveo camera is detected
```
$ lsusb
Bus 001 Device 002: ID 054c:0281 Sony Corp. 
Bus 001 Device 007: ID 1871:1301 Aveo Technology Corp. 

```
then it identifies as video0
```
~ $ ls -ltr /dev/video*
crwxrwxrwx+ 1 root video 81, 0 Jan 31 17:16 /dev/video0

```
when I run gstreamer-properties I get 
```
~ $ gstreamer-properties
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not open device '/dev/video0' for reading and writing. [v4l2_calls.c(511): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Device or resource busy]

```
and with Cheese:
```
~ $ cheese
** Message: cheese-application.vala:291: Error during camera setup: No device found


(cheese:3401): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:3401): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(cheese:3401): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:3401): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:3401): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:3401): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed


```
Am I missing a driver for this camera?
Thanks for your help!

---

### Post by Vladlenin5000 on 2016-01-31
Hi and welcome.

Try disconnecting and reconnecting and/or a different USB port.
It isn't a drivers (or lack of drivers) issue.

---

### Post by francois_baret on 2016-02-01
I have tried other USB, to no avail.
Why do you think it is not a driver problrm?

---

### Post by Vladlenin5000 on 2016-02-01
> **francois_baret said:**
> Why do you think it is not a driver problrm?

Because
```
Error running pipeline 'Video for Linux 2 (v4l2)': [COLOR=#ff0000]Could not open device '/dev/video0' for reading and writing.[/COLOR] [v4l2_calls.c(511): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1: system error: Device or resource busy
```

Are you using it in USB3.0 ports? Most likely it won't work at all unless connected to an USB2.0, like so many other cams.

---

