---
title: "Enter USB TV tuner card installation please help"
date: 2010-10-18
forum: Hardware
---

### Post by ggshastri on 2010-10-18
I have just now loaded ubuntu 10 and not able to find my Enter TV Tuner  card.

the lsusb command is giving me the following result.

Bus 006 Device 003: ID 6000:560a  
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:663e Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

if i dont attach the card the result is 

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:663e Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone help how i can use this to view TV on my laptop

---

### Post by IcarusR on 2010-10-18
Unplug tv stick, wait a few minutes, replug it in, then from a terminal run

```
dmesg
```

Check to see if there is any mention of it in the last dozen or so lines.

Can you post exact make & model.

Need to find exact chipset to see if it is supported.

Info on linux tv here

[http://linuxtv.org/wiki/index.php/Main_Page]("http://linuxtv.org/wiki/index.php/Main_Page")

---

### Post by ggshastri on 2010-10-19
This what are some lines of dmesg command

[ 6488.084099] usb 3-1: new low speed USB device using ohci_hcd and address 24
[ 6488.492075] usb 3-1: device not accepting address 24, error -62
[ 6488.668114] usb 3-1: new low speed USB device using ohci_hcd and address 25
[ 6489.076097] usb 3-1: device not accepting address 25, error -62
[ 6489.076133] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 6489.076216] usb 6-1: USB disconnect, address 7
[ 6489.316170] usb 6-1: new high speed USB device using ehci_hcd and address 8
[ 6489.760009] usb 6-1: configuration #1 chosen from 1 choice
[ 6506.584090] usb 6-1: USB disconnect, address 8
[ 6510.640094] usb 6-1: new high speed USB device using ehci_hcd and address 9
[ 6511.086758] usb 6-1: configuration #1 chosen from 1 choice
[ 6511.508126] usb 3-1: new low speed USB device using ohci_hcd and address 26
[ 6511.688092] usb 3-1: device descriptor read/64, error -62
[ 6511.972090] usb 3-1: device descriptor read/64, error -62
[ 6512.252102] usb 3-1: new low speed USB device using ohci_hcd and address 27
[ 6512.432098] usb 3-1: device descriptor read/64, error -62
[ 6512.716093] usb 3-1: device descriptor read/64, error -62
[ 6512.985132] usb 3-1: new low speed USB device using ohci_hcd and address 28
[ 6513.393125] usb 3-1: device not accepting address 28, error -62
[ 6513.568095] usb 3-1: new low speed USB device using ohci_hcd and address 29
[ 6513.980066] usb 3-1: device not accepting address 29, error -62
[ 6513.980097] hub 3-0:1.0: unable to enumerate USB device on port 1

---

### Post by ggshastri on 2010-10-19
I dont have much info abt the TV tuner card..... i presume it is a china made and this is what is written in the manual. It is a USB 2.0 TV STICK

Trident TV Master chiset and high quality sterio audio ADC....

---

### Post by ggshastri on 2010-10-19
hope this is the model No. E-220U, it is a indian made hardware

[this is the official website of the manufacturer and windows drivers are available there]("http://www.alibaba.com/product-free/105485881/ENTER_USB_2_0_TV_Stick.html")

[http://www.entermultimedia.com/support.html](http://www.entermultimedia.com/support.html)

---

