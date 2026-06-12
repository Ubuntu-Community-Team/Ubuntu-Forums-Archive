---
title: "M-Audio Transit detected, no sound"
date: 2009-07-29
forum: Hardware
---

### Post by carrett on 2009-07-29
Hi all,

I've tried a few guides from around the 'net to get my 5.1 speakers working via this M-Audio Transit USB dongle.

The device shows up fine in lsusb (the firmware's loaded in, it's not DFU):

```
Bus 002 Device 003: ID 0763:2006 Midiman M-Audio Transit
```And in /proc/asound/cards:

 ```
1 [USB            ]: USB-Audio - Transit USB
                      M-Audio Transit USB at usb-0000:00:1d.0-2, full speed
```

It even shows up in the gnome mixer and alsamixer, yet when I try to do a test sound from GNOME sound prefs or aplay a sound in /usr/share/sounds, nothing comes out. The speakers have a test function which I've used to verify that it's not a matter of turning up the volume or anything silly like that, so any clues you might have would be greatly helpful!

Thanks in advance!

---

### Post by carrett on 2009-07-30
Nevermind.

---

