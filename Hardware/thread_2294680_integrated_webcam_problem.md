---
title: "integrated webcam problem"
date: 2015-09-12
forum: Hardware
---

### Post by Bisneff on 2015-09-12
Hi everyone.

I'm on Asus n550-jv, with Ubuntu 14.04.

Here is my problem: after installing cheese my webcam worked fine, but sometimes something goes wrong and the webcam simply disappear! For bettere explain:

Cheese give error "There was an error playing video from webcam", and this is what terminal says:
> (cheese:9918): cheese-WARNING **: Internal data flow error.: gstbasesrc.c(2865): gst_base_src_loop (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin17/GstV4l2Src:video_source:
streaming task paused, reason error (-5)


** (cheese:9918): CRITICAL **: cheese_preferences_dialog_on_source_change: assertion '_tmp2_ > ((guint) 0)' failed

(cheese:9918): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:9918): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(cheese:9918): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:9918): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:9918): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:9918): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed



if I try to run gstreamer-proprieties it cannot find device /dev/video0. And if I try to run ls on /dev/ there isn't any video0, but video1. At this point, in gstreamer, if I try to change from video0 to video1 gstreamer gives error and in /dev/ video1 is disappeared and video2 is there...and so on :)

gstreamer error is:

>  Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(497): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]



Any idea?

---

### Post by Bisneff on 2015-09-14
up

---

