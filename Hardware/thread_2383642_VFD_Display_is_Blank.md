---
title: "VFD Display is Blank"
date: 2018-01-27
forum: Hardware
---

### Post by z7APXKm on 2018-01-27
Hi,

Hoping you can help me get my IMON VFD display working again.  

Ubuntu 16.04 LTS
Bus 001 Device 003: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver

/etc/LCDd.conf:

```

[Server]DriverPath = /usr/lib/x86_64-linux-gnu/lcdproc/
Driver = imon
#Driver = curses
Bind = 127.0.0.1
Port = 13666
ReportLevel = 2
ReportToSysLog = no
User = nobody
Foreground = no
#Message displayed before XBMC Starts, but after LCDProc starts
Hello = ". WELCOME TO  ."
Hello = ". KODI ."
#Message displayed if "OnExit" is set to "0" below.
Goodbye = ". Bye For ."
Goodbye = ". Now ."
#Time (in seconds) to display a screen.
WaitTime = 3
#"Yes" = Flash LCDProc Server Screen, "No" = Only show XBMC Info
ServerScreen = no
#"Open" = Client Controlled, "On" = Always On, "Off" = Always Off
Backlight = open
#"Open" = Client Controlled, "On" = Always On, "Off" = Always Off
Heartbeat = open
#Title Scrolling Speed. Valid values are "1" - "10"
TitleSpeed = 10


[imon]
#"0" = VFD Display, "1" = iMon LCD Display
Protocol = 0
#"0" = GoodBye message Displayed, "1" = Show Clock, "2" = Blank Device
OnExit = 1
#Path of the Output Device
Device = /dev/lcd0
#Screen contrast. Valid Values: "0" - "1000"
Contrast = 100
#LCD Screen Size (In Pixels)
Size = 96x16
#"On" = Backlight Turned On, "Off" = Backlight Always Off
Backlight = on
#"0" = 2 Disc Segments Spin, "1" = Their Complement Spins
DiscMode = 1

```

tail /var/log/kern.log
```
Jan 28 01:51:12 Myth kernel: [438872.027138] imon:vfd_write: invalid payload size

```

Nothing on the screen at all.  It has worked in the past, so I know it is connected up ok.

---

### Post by z7APXKm on 2018-01-28
OK, now it just shows: "_______Q"

My /etc/LCDd.conf file:

```

[Server]
#DriverPath = /usr/lib/lcdproc/
DriverPath = /usr/lib/x86_64-linux-gnu/lcdproc/
Driver = imon
Bind = 127.0.0.1
Port = 13666
ReportLevel = 2
ReportToSysLog = no
User = nobody
Foreground = no
#Message displayed before XBMC Starts, but after LCDProc starts
Hello = ". Powered By ."
Hello = ". XBMC ."
#Message displayed if “OnExit” is set to “0&#8243; below.
Goodbye = ". Thanks For ."
Goodbye = ". Using KODI! ."
#Time (in seconds) to display a screen.
WaitTime = 3
#”Yes” = Flash LCDProc Server Screen, “No” = Only show XBMC Info
ServerScreen = no
#”Open” = Client Controlled, “On” = Always On, “Off” = Always Off
Backlight = open
#”Open” = Client Controlled, “On” = Always On, “Off” = Always Off
Heartbeat = open
#Title Scrolling Speed. Valid values are “1&#8243; – “10&#8243;
TitleSpeed = 10



[imon]
#”0&#8243; = VFD Display, “1&#8243; = iMon LCD Display
Protocol = 1
#”0&#8243; = GoodBye message Displayed, “1&#8243; = Show Clock, “2&#8243; = Blank Device
OnExit = 1
#Path of the Output Device
#Device = /dev/lcd0
Device = /dev/input/by-id/usb-15c2_0036-event-mouse
#Screen contrast. Valid Values: “0&#8243; – “1000&#8243;
Contrast = 100
#LCD Screen Size (In Pixels)
Size = 96x16
#”On” = Backlight Turned On, “Off” = Backlight Always Off
Backlight = on
#”0&#8243; = 2 Disc Segments Spin, “1&#8243; = Their Complement Spins
DiscMode = 1

```


dmesg | grep -i imon
```

root@Myth:/var/log# dmesg | grep -i imon
[   19.895855] input: iMON Panel, Knob and Mouse(15c2:0036) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input10
[   19.924256] imon 1-1.1:1.0: imon_set_display_type: overriding display type to 1 via modparam
[   20.044264] Registered IR keymap rc-imon-pad
[   20.044356] input: iMON Remote (15c2:0036) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/rc/rc0/input11
[   20.044397] rc0: iMON Remote (15c2:0036) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/rc/rc0
[   20.064300] imon 1-1.1:1.0: iMON device (15c2:0036, intf0) on usb<1:3> initialized
[   20.064324] imon 1-1.1:1.1: iMON device (15c2:0036, intf1) on usb<1:3> initialized
[   20.064338] usbcore: registered new interface driver imon

```

---

### Post by chrisk2305 on 2018-02-13
I have exactly the same problem. Cannot get my VFD to work again. This is my VFD according to dmesg:

```


[   18.712437] imon 1-1:1.0: iMON device (15c2:ffdc, intf0) on usb<1:2> initialized
[   18.712481] usbcore: registered new interface driver imon



```

---

