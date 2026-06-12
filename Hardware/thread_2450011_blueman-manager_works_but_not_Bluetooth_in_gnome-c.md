---
title: "blueman-manager works but not Bluetooth in gnome-control-center"
date: 2020-09-05
forum: Hardware
---

### Post by boast on 2020-09-05
Anyone have any ideas why using [FONT=Courier New]blueman-manager[/FONT] works fine, but going to Bluetooth in the [FONT=Courier New]gnome-control-center[/FONT] says "No Bluetooth Found" ?

Terminal doesn't really say much

```

gnome-control-center -v bluetooth

(gnome-control-center:936464): GLib-CRITICAL **: 12:34:32.000: g_variant_get_type: assertion 'value != NULL' failed
(gnome-control-center:936464): GLib-CRITICAL **: 12:34:32.000: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
(gnome-control-center:936464): GLib-CRITICAL **: 12:34:32.000: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
...
12:34:32.0127                      GLib:    DEBUG: setenv()/putenv() are not thread-safe and should not be used after threads are created
12:34:32.0135                    (null):    DEBUG: No extra argument
12:34:32.0137                 Bluetooth:    DEBUG: Not adding device 'xxx'
12:34:32.0137                 Bluetooth:    DEBUG: Not interested in device 'xxx'
12:34:32.0137                 Bluetooth:    DEBUG: Default adapter changed to: /org/bluez/hci0
12:34:32.0155        bluetooth-cc-panel:    DEBUG: Updating airplane mode: BluetoothHasAirplaneMode 0, BluetoothHardwareAirplaneMode 0, BluetoothAirplaneMode 0, AirplaneMode 0
12:34:32.0156        bluetooth-cc-panel:    DEBUG: No Bluetooth available
12:34:32.0156                 Bluetooth:    DEBUG: Default adapter changed to: /org/bluez/hci0
12:34:32.0158        bluetooth-cc-panel:    DEBUG: Updating airplane mode: BluetoothHasAirplaneMode 0, BluetoothHardwareAirplaneMode 0, BluetoothAirplaneMode 0, AirplaneMode 0
12:34:32.0158        bluetooth-cc-panel:    DEBUG: No Bluetooth available
12:34:32.0158                 Bluetooth:    DEBUG: Unhandled UUID cbbfe0e1-f7f3-4206-123-213(0xcbbfe0e1)
12:34:32.0158                 Bluetooth:    DEBUG: Adding device (null) (/org/bluez/hci0/dev_43_12_13_23_23_23)
12:34:32.0159                 Bluetooth:    DEBUG: Saving device type Unknown for 43:E1:23:23:23:23
12:34:32.0159                 Bluetooth:    DEBUG: Unhandled UUID 00003456-0000-1000-123-123 (0x3456)
12:34:32.0159                 Bluetooth:    DEBUG: Adding device SHIELD (/org/bluez/hci0/dev_6D_F8_12_12_23_23)
12:34:32.0159                 Bluetooth:    DEBUG: Saving device type Unknown for 6D:F8:92:23:23:23
12:34:32.0160                 Bluetooth:    DEBUG: Adding device (null) (/org/bluez/hci0/dev_65_23_12_12_32_32)
...

```

---

