---
title: "Integrated DVD-ROM won't open"
date: 2019-02-17
forum: Hardware
---

### Post by sf6 on 2019-02-17
Hello,

I have a Panasonic CF-SX3 Haswell based notebook with Ubuntu 18.10 running.
My problem is, that I can't get the integrated DVD drive to open when I press the eject button.

Let me explain:

In the BIOS I can turn the drive on or off. If I turn it on, it works fine, but then the drive never shuts down and drains the battery. The recommended default setting therefore is "off" and have the OS turn it on when needed (that is, once I press the eject button). This works as intended in Windows but Ubuntu seems to have trouble resuming the DVD drive.

This might be related to a error message in Gnome notifications  that sometimes plops up concerning suspend. 

I've run  dbus-monitor interface='org.freedesktop.Notifications' > gsdpower.log which gives me:

```
method call time=1550419005.599077 sender=:1.129 -> destination=:1.21 serial=2134 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=CloseNotification
   uint32 3
signal time=1550419005.600817 sender=:1.21 -> destination=(null destination) serial=1555 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=NotificationClosed
   uint32 3
   uint32 3
signal time=1550419005.602046 sender=:1.21 -> destination=(null destination) serial=1557 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=NotificationClosed
   uint32 3
   uint32 2
method call time=1550427515.189983 sender=:1.44 -> destination=:1.21 serial=321 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=GetServerInformation
method call time=1550427515.190874 sender=:1.44 -> destination=:1.21 serial=322 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=Notify
   string "Power"
   uint32 0
   string ""
   string "Automatic suspend"
   string "Computer will suspend very soon because of inactivity."
   array [
   ]
   array [
      dict entry(
         string "urgency"
         variant             byte 2
      )
   ]
   int32 0
method call time=1550427524.145617 sender=:1.44 -> destination=:1.21 serial=323 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=CloseNotification
   uint32 4
signal time=1550427524.149542 sender=:1.21 -> destination=(null destination) serial=1685 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=NotificationClosed
   uint32 4
   uint32 3
signal time=1550427524.152220 sender=:1.21 -> destination=(null destination) serial=1686 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=NotificationClosed
   uint32 4
   uint32 2
```

Help would be appreciated :)

---

