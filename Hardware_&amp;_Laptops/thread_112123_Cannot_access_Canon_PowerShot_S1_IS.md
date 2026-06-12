---
title: "Cannot access Canon PowerShot S1 IS"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by LacteuS on 2006-01-03
Hi !

I can't access to my digital camera Canon PowerShot S1 IS :

- with gthumb : impossible
- with gphoto2 : impossible

```
# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 013: ID 04a9:309c Canon, Inc. PowerShot S1 IS
Bus 001 Device 001: ID 0000:0000

```

```
# gphoto2 --list-cameras | grep "PowerShot S1"
        "Canon PowerShot S1 IS (normal mode)"
        "Canon PowerShot S1 IS (PTP mode)"
        "Canon PowerShot S10"
        "Canon PowerShot S100"
        "Canon PowerShot S110"

```

```

# ls /dev/sd*
zsh: no matches found: /dev/sd*

```

```

# env LANG=C gphoto2 --debug -L
[...lot of information...]

1.893716 gphoto2-port(2): Reading 64=0x40 bytes from port...
6.897810 canon/usb.c(2): canon_usb_dialogue: read 1 of 0x40 bytes failed! (Error reading from the port)
6.897860 context(0): lock keys failed.

*** Error ***
lock keys failed.
6.897905 gphoto2-port(2): Closing port...
*** Error (-114: 'OS error in camera communication') ***

6.900204 gp-camera(2): Freeing camera...
6.900231 gphoto2-port(2): Freeing port...
6.900249 gphoto2-port(2): Closing port...
6.900326 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
6.900345 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
6.900362 gphoto2-filesystem(2): Internally deleting all folders from '/'...

```

I REALLY don't understand anything about the "lock keys failed"...
Please, help me !

---

### Post by %hMa@?b&lt;C on 2006-01-03
doesn't  it auto mount as a usb mass storage.  Both mine and my dad's cameras do that.
edit: googled it and found this
```
Canon PowerShot S1 IS 	0x04a9/0x309c
	CF II 	PTP (usb)
gphoto2/ptp (usb)
gphoto2/canon (usb) 
``` [http://www.teaser.fr/~hfiguiere/linux/digicam.html](http://www.teaser.fr/~hfiguiere/linux/digicam.html)
that says what you need i hope

---

### Post by fsanders on 2006-01-11
I have a Canon Powershot A620 and it did not show up as a usb mass storage device like my previous camera did.  I ended up installing digikam and it worked perfectly.

---

