---
title: "check battery level of bluetooth devices."
date: 2023-02-24
forum: Hardware
---

### Post by luca-dgh on 2023-02-24
[LEFT][COLOR=#232629][FONT=-apple-system]Reading [this thread]("https://askubuntu.com/questions/1117563/check-bluetooth-headphones-battery-status-in-linux") I could capture the battery level of my bt devices on my laptop. But is not working on my desktop with the same devices, because upower (and/or DBUS I suppose) doesn't recognize them, bluetoothctl does.
How to fix this?
[/FONT][/COLOR][/LEFT]
```
luca@laptop-luca:~$ uname -a
Linux laptop-luca 5.15.0-60-generic #66-Ubuntu SMP Fri Jan 20 14:29:49 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

```[LEFT][COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
[/LEFT]
```
luca@pc-sala:~$ bluetoothctl
Agent registered
[Philips BT2200]# devices
Device A4:77:58:7B:56:FF Philips SHB3075
Device 40:EF:4C:FA:15:2B Philips BT2200
[Philips BT2200]# exit
```[LEFT][COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR][/LEFT]
```
luca@pc-sala:~$ upower -d
Device: /org/freedesktop/UPower/devices/keyboard_hidpp_battery_0
  native-path:          hidpp_battery_0
  model:                Wireless Keyboard
  serial:               4023-00-00-00-00
  power supply:         no
  updated:              lun 20 feb 2023 17:42:00 (7 seconds ago)
  has history:          yes
  has statistics:       yes
  keyboard
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    battery-level:       normal
    percentage:          55% (should be ignored)
    icon-name:          'battery-low-symbolic'

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         no
  updated:              lun 20 feb 2023 17:31:34 (633 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       none
    percentage:          0%
    icon-name:          ''

Daemon:
  daemon-version:  0.99.17
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  no
  critical-action: HybridSleep
luca@pc-sala:~$ 
```[LEFT][COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR][/LEFT]

---

