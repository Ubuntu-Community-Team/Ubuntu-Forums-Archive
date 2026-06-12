---
title: "Webcam not working on Samsung Series 7"
date: 2013-05-21
forum: Hardware
---

### Post by EddyTheB on 2013-05-21
Hi, I have a Samsung Series 7 Chronos, model number NP700Z5C-SO2UB, with Ubuntu 13.04, and the internal webcam doesn't work.

Following advice for others who had similar problems I installed Cheese, and started it from the terminal:

```

$ cheese

** (cheese:8891): WARNING **: cheese-main.vala:251: Error: No device found


(cheese:8891): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:8891): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(cheese:8891): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion `value != NULL' failed

(cheese:8891): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

(cheese:8891): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:8891): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion `device != NULL' failed

```

And then I did 
```

$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07da Intel Corp. 

```

So there's no sign that the system even knows I have a webcam. I never tried it in windows before I uninstalled it, so I don't know if it's ever worked. Any suggestions?

---

