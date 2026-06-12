---
title: "USB Audio device not detected in lsusb"
date: 2010-02-07
forum: Hardware
---

### Post by haaglin on 2010-02-07
Hi. 

I bought the same usb audio device as shown in this page:

[http://www.hermann-uwe.de/blog/playing-audio-on-the-nslu2]("http://www.hermann-uwe.de/blog/playing-audio-on-the-nslu2")

However, mine doesnt show up in lsusb. So it doesnt work. This is the dmesg log: 
```

[  722.672566] usb 5-1: new full speed USB device using uhci_hcd and address 27
[  722.800077] usb 5-1: device descriptor read/64, error -71
[  723.030065] usb 5-1: device descriptor read/64, error -71
[  723.260091] usb 5-1: new full speed USB device using uhci_hcd and address 28
[  723.390082] usb 5-1: device descriptor read/64, error -71
[  723.632580] usb 5-1: device descriptor read/64, error -71
[  723.862590] usb 5-1: new full speed USB device using uhci_hcd and address 29
[  724.280073] usb 5-1: device not accepting address 29, error -71
[  724.400078] usb 5-1: new full speed USB device using uhci_hcd and address 30
[  724.820060] usb 5-1: device not accepting address 30, error -71
[  724.820083] hub 5-0:1.0: unable to enumerate USB device on port 1


```

I'm runnning a 64bit kernel if it makes a difference: 
```
Linux 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
```

Does this mean that my usb card is broken, or is this card not supported in ubuntu? As seen in the previous link, this does work in Debian Linux 2.6.18 using the snd_usb_audio kernel module.

Thanks in advance.

---

