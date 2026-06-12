---
title: "bluetooth headphones paired but not connected"
date: 2016-04-09
forum: Hardware
---

### Post by Max_S on 2016-04-09
Hi all,

I recently bought the Bose® SoundLink® around-ear wireless headphones II and tried to connect them to my laptop but it didn't work. I have Ubuntu 15.10 installed on a ThinkPad T440s and use the blueman bluetooth manager to connect to my devices.
Here is the log from bluetooth-manager if that is any help:

```

Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:170)
Bose AE2 SoundLink 
_________
on_device_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:161)
list: device_prop_ch Paired 1 /org/bluez/hci0/dev_08_DF_1F_C3_32_02 () {} 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:262)
row update event Paired 1 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:170)
Bose AE2 SoundLink 
_________
on_device_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:161)
list: device_prop_ch UUIDs dbus.Array([dbus.String(u'00001101-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001108-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110b-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110c-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111e-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001200-0000-1000-8000-00805f9b34fb')], signature=dbus.Signature('s'), variant_level=1) /org/bluez/hci0/dev_08_DF_1F_C3_32_02 () {} 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:262)
row update event UUIDs dbus.Array([dbus.String(u'00001101-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001108-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110b-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110c-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111e-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001200-0000-1000-8000-00805f9b34fb')], signature=dbus.Signature('s'), variant_level=1) 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:170)
Bose AE2 SoundLink 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:153)
adapter propery changed Discovering 0 
_________
on_device_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:161)
list: device_prop_ch Connected 0 /org/bluez/hci0/dev_08_DF_1F_C3_32_02 () {} 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:262)
row update event Connected 0 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:170)
Bose AE2 SoundLink 
_________
level_setup_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:323)
animating down 
_________
on_device_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:161)
list: device_prop_ch Connected 0 /org/bluez/hci0/dev_08_DF_1F_C3_32_02 () {} 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:262)
row update event Connected 0 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:170)
Bose AE2 SoundLink 
_________
update (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:184)
stopping monitor (not connected) 
connect

```

I set up the headphones as a new device, successfully paired it using a random key and then tried to connect to it as Headset (Audio Sink also doesn't work).

Any help is greatly appreciated.

Cheers,

Max

---

