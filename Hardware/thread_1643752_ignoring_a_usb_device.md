---
title: "ignoring a usb device"
date: 2010-12-12
forum: Hardware
---

### Post by phirestalker on 2010-12-12
ok I am trying to get ubuntu to ignore my iphone when I plug it in so I can use it with virtualbox, the problem is the iphone changes its id during a firmware restore. I am also trying to jailbreak it but the phone ignores the commands, I know it works on a real windows install, so it has to be linux interfering with the passthrough to virtualbox. Below are the contents of the files I have tried to get it to ignore the iphone by its vendor id only.

/etc/udev/rules.d/noiphone.rules
```
ATTRS{idVendor}=="05ac", OPTIONS=="ignore_device"
```

/etc/hal/fdi/preprobe/10-iphone.fdi
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
<device> 
<match key="usb.vendor_id" int="1452">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>
```

/etc/modprobe.d/usbhid.conf
```
options usbhid quirks=0×05ac:0×1297:0×04
options usbhid quirks=0×05ac::0×04

```

I really don't know what else to try because gnome still pops up that the iphone is connected and tries to communicate with it. from what I understand a /dev entry is only created when a driver is loaded so I don't even want a /dev entry virtualbox should pick is up directly from usb. Thanks for any help

---

