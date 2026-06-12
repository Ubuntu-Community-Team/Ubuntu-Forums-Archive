---
title: "Logitech g703 battery level reporting"
date: 2019-10-21
forum: Hardware
---

### Post by draki on 2019-10-21
Hello - I'm hoping someone can help me
I have a Logitech g703 mouse connected through a Lightspeed received and would like a command to report the battery level. I realise that this hasn't been possible until Kernel version 5+, but I'm now on 19.10 with the latest kernel and was expecting `upower -d` to report the battery level, but it doesn't

I've also been looking at ratbagctl - but no battery information is being reported by that either

Any suggestions? Thanks very much in advance

---

### Post by #&amp;thj^% on 2019-10-21
You can install the "Solaar" program with a GUI interface.
```
sudo apt install solaar
```
Or cli with: 
```
upower --dump
```
Not quite as elegant as Solaar though.

---

### Post by draki on 2019-10-21
Thanks for the reply.. Solaar doesn't work ("battery level unavailable") and nor does upower --dump

```
$ solaar show
Unifying Receiver
  Device path  : /dev/hidraw10
  USB id       : 046d:c539
  Serial       : 4CA99F7C
    Firmware   : 39.04.B0036
    Bootloader : 02.09
    Other      : AA.BE
  Has 1 paired device(s) out of a maximum of 1.
  Notifications: wireless, software present (0x000900)
  Device activity counters: (empty)

  1: G703 Wired/Wireless Gaming Mouse
     Codename     : G703
     Kind         : mouse
     Wireless PID : 4070
     Protocol     : HID++ 4.2
     Polling rate : 8 ms (125Hz)
     Serial number: AFE674F7
          Firmware: MPM 14.02.B0007
        Bootloader: BOT 64.02.B0007
             Other: 
     The power switch is located on the base.
     Supports 29 HID++ 2.0 features:
         0: ROOT                   {0000}   
         1: FEATURE SET            {0001}   
         2: DEVICE FW VERSION      {0003}   
         3: DEVICE NAME            {0005}   
         4: unknown:1001           {1001}   
         5: unknown:1863           {1863}   internal, hidden
         6: unknown:18A1           {18A1}   internal, hidden
         7: unknown:1E00           {1E00}   hidden
         8: unknown:1E20           {1E20}   
         9: unknown:1EB0           {1EB0}   internal, hidden
        10: ADJUSTABLE DPI         {2201}   
        11: ANGLE SNAPPING         {2230}   
        12: SURFACE TUNING         {2240}   
        13: REPORT RATE            {8060}   
        14: ONBOARD PROFILES       {8100}   
        15: MOUSE BUTTON SPY       {8110}   
        16: unknown:1850           {1850}   internal, hidden
        17: unknown:00C2           {00C2}   
        18: unknown:1801           {1801}   internal, hidden
        19: unknown:1802           {1802}   internal, hidden
        20: unknown:1803           {1803}   internal, hidden
        21: unknown:1890           {1890}   internal, hidden
        22: unknown:1811           {1811}   internal, hidden
        23: unknown:8111           {8111}   
        24: COLOR LED EFECTS       {8070}   
        25: unknown:1809           {1809}   
        26: unknown:1830           {1830}   internal, hidden
        27: unknown:1805           {1805}   internal, hidden
        28: unknown:1806           {1806}   internal, hidden
     Battery status unavailable.

```

It seems like the mouse/ receiver isn't recognised by upower:
```
$ upower --dump
Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         no
  updated:              Mon 21 Oct 2019 13:34:41 BST (20165 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       none
    icon-name:          'battery-missing-symbolic'

Daemon:
  daemon-version:  0.99.11
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  no
  critical-action: PowerOff
```

Any further suggestions?

---

### Post by #&amp;thj^% on 2019-10-21
Well if you could of seen your battery, it would of went like:
```
upower -i /org/freedesktop/UPower/devices/mouse_hidpp_battery_0
  native-path:          hidpp_battery_0
  model:                M510
  serial:               1025-5f-c3-cb-e4
  power supply:         no
  updated:              Mon 21 Oct 2019 12:16:00 PM MDT (100 seconds ago)
  has history:          yes
  has statistics:       yes
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    battery-level:       normal
    percentage:          55% (should be ignored)
    icon-name:          'battery-low-symbolic'

```
That output of yours has me stumped ATM.
I'm not sure the device has support just this yet.:( I think it has to do with Bluetooth version of device)

---

### Post by draki on 2019-10-21
Yeah - that's what I would have expected :(  
I also posted on Solaar's github and just got a response that they know they need to add support for it: [https://github.com/pwr-Solaar/Solaar/issues/570](https://github.com/pwr-Solaar/Solaar/issues/570)
Hopefully they'll add support soon

---

### Post by #&amp;thj^% on 2019-10-21
Thanks for your efforts, I like the pro-active attitude.
Kind Regards, and if you think of it, It will help others here if you update your thread, when relevant.

---

### Post by draki on 2019-10-21
Thanks :) and will do

---

### Post by jimmyrus on 2019-10-22
I got nothing to solve the problem but can confirm its not just that device. My apple mouse used to report battery now it doesn't same with my logitech mx.

---

### Post by draki on 2019-10-25
Looks like support is coming in kernel 5.4 [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-HID](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-HID)

> Support for the Logitech G700/G700s receivers as well as the Logitech Lightspeed receiver.

Hopefully..

---

