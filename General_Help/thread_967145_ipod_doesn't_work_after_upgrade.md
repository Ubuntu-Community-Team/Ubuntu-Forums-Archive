---
title: "ipod doesn't work after upgrade"
date: 2008-11-01
forum: General Help
---

### Post by dumbmatter on 2008-11-01
i just upgraded to 8.10, and now my ipod doesn't work.  i plug it in, it shows up on the desktop for a second, and then the icon goes away.  here is the output of running the "ipod" command and then plugging in my ipod:
```
** Message: Device Added: /org/freedesktop/Hal/devices/volume_uuid_890C_F46A
Path Info
   Device Path:      /dev/sdb2
   Mount Point:      /media/JEREMY'S IP
   Control Path:     /media/JEREMY'S IP/iPod_Control/
   HAL ID:           /org/freedesktop/Hal/devices/volume_uuid_890C_F46A
Device Info
   Model Number:     A448
   Device Model:     Video (Black)
   iPod Generation:  Fifth (5)
   Adv. Capacity:    80 GB
   Is New:           YES
   Writable:         YES
   Serial Number:    8K6412FXV9R
   Firmware Version: (null)
   Manufacturer ID:  8K
   Production Year:  2006
   Production Week:  41
   Production Index: 2855
Volume Info
   Volume Size:      79883919360
   Volume Used:      10040942592
   Available         69842976768
   UUID:             890C-F46A
   Label             JEREMY'S IP
User-Provided Info
   Device Name:      (null)
   User Name:        (null)
   Host Name:        (null)
Supported Artwork Formats
   Cover:            200x200
   Cover:            100x100
   Photo:            50x41
   Photo:            320x240
   Photo:            130x88
   Photo:            640x480

** Message: Device Removed: /org/freedesktop/Hal/devices/volume_uuid_890C_F46A
```
so it looks like it recognizes the device and then removes it instantly?  i have no idea where to even start debugging this.  can anyone help me?

---

