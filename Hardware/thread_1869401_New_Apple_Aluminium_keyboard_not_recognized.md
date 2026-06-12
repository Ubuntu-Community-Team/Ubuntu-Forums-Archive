---
title: "New Apple Aluminium keyboard not recognized"
date: 2011-10-25
forum: Hardware
---

### Post by sin.pecado on 2011-10-25
Hi, 

I have a pretty new Apple aluminum keyboard which I can't get properly recognized. 
```
$ lsusb | grep 05ac
Bus 001 Device 067: ID 05ac:024f 
Bus 001 Device 066: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
```

The device ID of the new and older keyboard doesn't (the ID of the USB hub macthces, though) - I have one the old ones as well:
```
$ lsusb | grep 05ac
Bus 001 Device 067: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 001 Device 066: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
```

While the latter, as you can see, gets recognized and the multimedia keys do work, with the new model they don't pretty annoying as I've gotten used to them quite a bit.

I've tried updating the [FONT="Courier New"]usb.ids[/FONT], but even pretty up-to-date lists ([like the one from usbutils]("https://github.com/gregkh/usbutils/blob/master/usb.ids")) don't contain [FONT="Courier New"]05ac:024f[/FONT]. 

I've also tried to "hack" the [FONT="Courier New"]usb.ids[/FONT] by adding a the line
```

	024f  Aluminum Keyboard (ISO)

```
which didn't work, I kept on getting an [FONT="Courier New"]"Uknown line at line ..."[/FONT] error when running [FONT="Courier New"]lsusb[/FONT].

Also tried simply replacing the ID [FONT="Courier New"]0221[/FONT] with [FONT="Courier New"]024f[/FONT], in this case the device name shows up correctly with [FONT="Courier New"]lsusb[/FONT], [FONT="Courier New"]/sys/module/hid_apple/[/FONT] is created, but the multimedia keys still don't work. 

Any idea how to fix or work around this issue?

Cheers,
Sz.

Edit: not very relevant, but my OS is:
```

$ lsb_release -d
Description:	Ubuntu 10.04.3 LTS

```

---

