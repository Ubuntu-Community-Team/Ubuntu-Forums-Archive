---
title: "Creative Soundblaster play! 2 USB Sound card is supported?"
date: 2016-02-15
forum: Hardware
---

### Post by Beer_Town on 2016-02-15
I'm thinking to buy this:

[http://us.creative.com/p/sound-blaster/sound-blaster-play-2](http://us.creative.com/p/sound-blaster/sound-blaster-play-2)

Its USB id should be 041e:323d
Does somebody already use it with Linux? Is it supported?

thank you very much!

---

### Post by lypserv on 2016-04-23
Hey.

Yes, it is. Out of the box:

```

[230043.324099] usbcore: registered new interface driver snd-usb-audio
[230043.652736] usb 3-2: new full-speed USB device number 4 using xhci_hcd
[230044.008096] input: Creative Technology Ltd Sound Blaster Play! 2 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.3/0003:041E:323D.0005/input/input24
[230044.059778] hid-generic 0003:041E:323D.0005: input,hiddev0,hidraw4: USB HID v1.00 Device [Creative Technology Ltd Sound Blaster Play! 2] on usb-0000:00:14.0-2/input3

```

---

