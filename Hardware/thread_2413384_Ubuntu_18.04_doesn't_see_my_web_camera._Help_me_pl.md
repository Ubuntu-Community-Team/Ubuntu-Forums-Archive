---
title: "Ubuntu 18.04 doesn't see my web camera. Help me please"
date: 2019-02-25
forum: Hardware
---

### Post by alexmate18 on 2019-02-25
Hello guys. There is a problem with my camera. I used Ubuntu 16.04 and this OS could see my web camera. Then I changed my OS to Ubuntu 18.04 and now it doesn't see the web cam. What's the problem? I also tried both 16.04 and 18.04 liveCD and only the first one sees my web cam.

4.15.0-29-generic #31~16.04.1-Ubuntu SMP Wed Jul 18 08:54:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux works correctly with the camera.
4.15.0-**45**-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux doesn't.

How to stay on Ubuntu 18.04 but to use my camera? Any suggestions please?
The OS determine my cam as Bus 002 Device 004: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
My cam is Canyon CNR-WCAM43G 

There is a possibility that the developers did not include the old drivers for the new kernel version and IDK why.
Skype and Cheese don't see the cam as well. I tried the commands cheese and cheese /dev/video0
```
user@user:~$ cheese

(cheese:5334): Gtk-WARNING **: 21:45:42.851: Theme parsing error: cheese.css:7:35: The style property GtkScrollbar:min-slider-length is deprecated and shouldn't be used anymore. It will be removed in a future version
** Message: 21:45:42.931: cheese-application.vala:211: Error during camera setup: No device found


(cheese:5334): cheese-CRITICAL **: 21:45:42.943: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:5334): GLib-CRITICAL **: 21:45:42.943: g_variant_new_string: assertion 'string != NULL' failed

(cheese:5334): GLib-CRITICAL **: 21:45:42.943: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:5334): GLib-GIO-CRITICAL **: 21:45:42.943: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:5334): GLib-CRITICAL **: 21:45:42.943: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:5334): GLib-GIO-CRITICAL **: 21:45:42.943: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:5334): GLib-CRITICAL **: 21:45:42.943: g_variant_unref: assertion 'value != NULL' failed

** (cheese:5334): CRITICAL **: 21:45:42.943: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed

```
```
user@user:~$ uname -a
4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
user@user:~$ snap list
Name         Version    Rev   Tracking  Publisher   Notes
core         16-2.37.2  6405  stable    canonical&#10003;  core
hello-world  6.3        27    stable    canonical&#10003;  -
```


Help me please.

---

