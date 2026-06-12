---
title: "Wireless Mouse and Keyboard - mouse not working"
date: 2010-03-15
forum: Hardware
---

### Post by perham on 2010-03-15
hi,
I've recently installed ubuntu ppc on my ps3 and I have connected my A4tech wireless mouse and keyboard to it. t connects using a dongle which then connects to the keyboard and mouse. the problem is that although the keybord is working, the mouse is not. I've tested it elsewere and it works. but in this system, only keyboard works. any ideas?



```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 004: ID 09da:024f A4 Tech Co., Ltd [COLOR="Red"]<< this is the wireless set[/COLOR]
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 002: ID 05e3:0607 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0267 Sony Corp. Tachikoma Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by perham on 2010-03-15
> **perham said:**
> hi,
I've recently installed ubuntu ppc on my ps3 and I have connected my A4tech wireless mouse and keyboard to it. t connects using a dongle which then connects to the keyboard and mouse. the problem is that although the keybord is working, the mouse is not. I've tested it elsewere and it works. but in this system, only keyboard works. any ideas?



```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 004: ID 09da:024f A4 Tech Co., Ltd [COLOR="Red"]<< this is the wireless set[/COLOR]
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 002: ID 05e3:0607 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0267 Sony Corp. Tachikoma Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

here's the result of ls /dev/input/by-id
```
usb-A4Tech_RF_USB_Receiver-event-kbd	
usb-A4Tech_RF_USB_Receiver-event-mouse
usb-A4Tech_RF_USB_Receiver-mouse

```

so the mouse is recognised. when I use cat to get the streamed data, and I move my mouse, the data is coming from the mouse. so it seems more like a Xserver bug. why isn't it recognising the coming data and moving the pointer?

---

### Post by perham on 2010-03-15
solved the issue by removing xserver-xorg-input-synaptics. it seems like a bug/conflict there.

---

