---
title: "USB Headset, Mic works, headphones don't"
date: 2009-05-20
forum: Hardware
---

### Post by ajm4481 on 2009-05-20
I've got an USB Headset logitech headset/mic
 
It shows up in lsusb just fine:
```

Bus 001 Device 006: ID 0bda:0116 Realtek Semiconductor Corp. Mass 
Storage Device
Bus 001 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, 
VX2S, V1S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:0a0b Logitech, Inc.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 
2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I managed to get the mic to work by changing alsa mixer and the sound 
preferences correctly. It also works perfectly in Gnome Sound Recorder!
 
But somehow I can't get the headphone part of my headset to work. It 
simply keeps playing the sound over my laptop speakers. I know the 
headphones are not broken.
 
I have no idea on how I can make the headphones work, can you help me?
 
PS: I'm using Ubuntu 9.04, a fresh install.

---

