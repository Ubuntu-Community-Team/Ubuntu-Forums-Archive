---
title: "Bluetooth suddenly stopped working"
date: 2013-03-09
forum: Hardware
---

### Post by funkdified on 2013-03-09
Hi, I booted up my computer yesterday and found I couldn't discover new bluetooth devices.. It works fine when booting into Windows, so I know my radio didn't die.

I'm using a VIZIO CT15-A5 laptop...

Here are some outputs for you:

```
funkdified@vizio ~ $ sudo bluetoothd -d -n
bluetoothd[2603]: Bluetooth daemon 4.101
bluetoothd[2603]: src/main.c:parse_config() parsing main.conf
bluetoothd[2603]: src/main.c:parse_config() discovto=0
bluetoothd[2603]: src/main.c:parse_config() pairto=0
bluetoothd[2603]: src/main.c:parse_config() pageto=8192
bluetoothd[2603]: src/main.c:parse_config() auto_to=60
bluetoothd[2603]: src/main.c:parse_config() name=%h-%d
bluetoothd[2603]: src/main.c:parse_config() class=0x000100
bluetoothd[2603]: src/main.c:parse_config() Key file does not have key 'DeviceID'
D-Bus setup failed: Name already in use
bluetoothd[2603]: Unable to get on D-Bus
```

```

blueman-browse
Loading configuration plugins
_________
SetAdapter (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:301)
None 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:180)
adapter propery changed Discovering 1 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:180)
adapter propery changed Discovering 0 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:180)
adapter propery changed Discovering 1 
_________
destroy (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:128)
destroying 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceSelectorWidget.py:81)
Deleting widget 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:63)
deleting mainlist 
```


```
funkdified@vizio ~ $ rfkill list
0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no
1: hci0: Bluetooth
   Soft blocked: no
   Hard blocked: no
```

Any help would be greatly appreciated. Not sure how it just died suddenly!

---

### Post by funkdified on 2013-03-19
Hi just wondering if anyone has had a chance to look at this? Thanks !

---

### Post by funkdified on 2013-03-20
Please help!

---

