---
title: "Mounted USB Drive"
date: 2008-12-01
forum: General Help
---

### Post by chrislynch8 on 2008-12-01
Hi,

How can I test that a USB device has been mounted to this folder /media/usbdrive.

For automated backups I want my script to check that the USB Device is mounted. The device is generally /dev/sdc1 but this can change - is it possible to say

I can see in /proc/bus/usb/devices the references to my attached USB Device - is there a way to use this information?

if (device mounted to /media/usbdrive)
    continue
else
    alert someone


Thanks
Chris

---

### Post by lucasl on 2008-12-01
Perhaps a little 'hacky', but the way I'd do it is create a file (or use one) on the root of the drive then check for its existance.
Example (checks if my Vista drive is mounted):
```

if [ -f '/media/Vista/vstaldr.img' ]; then
  echo "Vista Drive present."
else
  echo "Vista drive not present."
fi

```

---

### Post by chrislynch8 on 2008-12-01
Ok so this USB-Drive is for backups so it will always have a set of root folders that will never change called serverXX etc.

Thanks, I'll test this out and how it handles.

Rgds
Chris

---

