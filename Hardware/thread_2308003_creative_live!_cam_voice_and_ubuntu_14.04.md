---
title: "creative live! cam voice and ubuntu 14.04"
date: 2015-12-30
forum: Hardware
---

### Post by jutu2 on 2015-12-30
Good day, want an advice!
camera doesn't work 
lsusb
Bus 001 Device 008: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 006: ID 125f:a94a A-DATA Technology Co., Ltd. 
Bus 001 Device 004: ID 03f0:2c17 Hewlett-Packard LaserJet 1022
Bus 001 Device 007: ID 041e:4045 Creative Technology, Ltd Live! Cam Voice
Bus 001 Device 005: ID 041e:4048 Creative Technology, Ltd 
Bus 001 Device 003: ID 041e:404b Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 192f:0916 Avago Technologies, Pte. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


cheese
** Message: cheese-application.vala:291: Error during camera setup: &#1059;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;&#1099;


(cheese:3609): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:3609): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(cheese:3609): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:3609): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:3609): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:3609): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed

---

