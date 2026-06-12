---
title: "No Sound HP Chromebook x360 11 G1 EE"
date: 2023-04-25
forum: Hardware
---

### Post by vlcplayerfan on 2023-04-25
so i was able to get lubuntu installed and it runs great on this chromebook and its faster then chrome os only problem is there is no audio anymore 
i tried from a live usb ubuntu and puppy linux and they also have no sound 

what can i do this is my friends chromebook and he really needs sound on it via the built in speakers

---

### Post by Yellow Pasque on 2023-04-27
Yeah, Chromebooks are no fun when trying to use the built in audio. And HP doesn't want you running "unsupported" OS's. A USB audio solution is your best bet.

---

### Post by Yellow Pasque on 2023-04-28
Something like this: [https://www.amazon.com/Computer-Speaker-Desktop-USB-Powered-External/dp/B09H65BHLT/ref=sr_1_8?keywords=usb%2Bspeakers&qid=1682711480&sr=8-8&th=1](https://www.amazon.com/Computer-Speaker-Desktop-USB-Powered-External/dp/B09H65BHLT/ref=sr_1_8?keywords=usb%2Bspeakers&qid=1682711480&sr=8-8&th=1)

```
Q: Does this work with Linux?
A: Yep, it absolutely works on Linux.

It shows up on the usb bus and is associated with the following drivers

&#10095; lsusb
Bus 001 Device 022: ID 1908:2070 GEMBIRD Honk HK-5002 USB Speaker
&#10095; lsusb -t
/: Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
|__ Port 2: Dev 13, If 0, Class=Hub, Driver=hub/2p, 480M
|__ Port 1: Dev 14, If 0, Class=Hub, Driver=hub/4p, 480M
|__ Port 3: Dev 17, If 0, Class=Hub, Driver=hub/4p, 480M
|__ Port 2: Dev 22, If 1, Class=Audio, Driver=snd-usb-audio, 12M
|__ Port 2: Dev 22, If 2, Class=Human Interface Device, Driver=usbhid, 12M
|__ Port 2: Dev 22, If 0, Class=Audio, Driver=snd-usb-audio, 12
```

---

