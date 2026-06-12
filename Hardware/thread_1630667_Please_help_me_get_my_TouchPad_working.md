---
title: "Please help me get my TouchPad working"
date: 2010-11-25
forum: Hardware
---

### Post by ghelbig on 2010-11-25
I'm running 10.04 LTS on my Lenovo V460.  The TouchPad does not work,

I had it working (mostly) at one point.  It recently stopped working - it may be related to an update, I'm not sure.

One help page said to use 'gpointing-device-settings'.  It doesn't like the TouchPad:

** (gpointing-device-settings:2035): CRITICAL **: gpds_ui_new: assertion `module != NULL' failed

** (gpointing-device-settings:2035): CRITICAL **: gpds_ui_is_available: assertion `GPDS_IS_UI(ui)' failed

(gpointing-device-settings:2035): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


The device is recognized, tpconfig can find it (but it doesn't seem to help, rather it makes it worse):[INDENT] sudo tpconfig
[sudo] password for ########: 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
[/INDENT]Right now it's doing nothing, except for occasionally moving the cursor to random locations when my hand gets near the space bar...

Please help.

---

