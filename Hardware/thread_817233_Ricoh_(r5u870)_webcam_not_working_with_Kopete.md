---
title: "Ricoh (r5u870) webcam not working with Kopete"
date: 2008-06-03
forum: Hardware
---

### Post by malachias on 2008-06-03
Hi

I have a Sony Vaio FE890 with a built-in motion-eye Ricoh webcam. lsusb returns:
```
Bus 005 Device 002: ID 05ca:1836 Ricoh Co., Ltd
```
I've compiled/installed the drivers and they work fine. Motion works perfectly, skype detects and can use my webcam, amsn likewise. However, Kopete won't find it. Under Configure -> Video, the combo-box next to Device is just empty.
Does anyone know how to fix this? (I'm on Kubuntu 8.04 Remix (i.e. kde4))

---

### Post by malachias on 2008-06-03
if it helps, this is what happens in the console when I click the "Video" icon under Settings:
```
kopete(21849) AVDeviceConfig::AVDeviceConfig: kopete:config (avdevice): KopeteAVDeviceConfigFactory::componentData() called.
kopete(21849) Kopete::AV::VideoDevicePool::open: open(): No devices found. Must scanfor available devices. 2077529056
kopete(21849) Kopete::AV::VideoDevicePool::scanDevices: called
kopete(21849) Kopete::AV::VideoDevicePool::scanDevices: exited successfuly
kopete(21849) Kopete::AV::VideoDevicePool::open: open(): No devices found. bailing out. 2077529056
kopete(21849) Kopete::AV::VideoDevicePool::setSize: VideoDevicePool::setSize() fallback for no device.
kopete(21849) Kopete::AV::VideoDevicePool::setSize: VideoDevicePool::setSize() buffer size:  230400
kopete(21849) Kopete::AV::VideoDevicePool::fillDeviceKComboBox: Called.
kopete(21849) Kopete::AV::VideoDevicePool::fillDeviceKComboBox: Combobox cleaned.
kopete(21849) Kopete::AV::VideoDevicePool::fillInputKComboBox: Called.
kopete(21849) Kopete::AV::VideoDevicePool::fillStandardKComboBox: Called.
kopete(21849) Kopete::AV::VideoDevicePool::startCapturing: startCapturing() called.
```
Anyone know why it can't find my webcam?
crw-rw---- 1 root video 81, 0 2008-06-03 12:50 /dev/video0

---

### Post by linux-trap on 2009-04-11
Hi, I have the same problem, any know a good solution ??

---

