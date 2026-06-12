---
title: "After the latest updates usb keyboard is dead"
date: 2009-08-03
forum: Hardware
---

### Post by barisurum on 2009-08-03
Hi, this problem appears to have happened after the latest updates (linux-image-2.6.28.14 and various other packages). 
The problem is that after the boot my logitech usb keyboard stays dead (unresponsive) for a period of time then it becomes functional after about 1 minute. It's a very annoying thing. 
Both keyboard and usb mice works fine in windows. but a very odd thing happens and after booting into XP windows says found new hardware and reinstalls the drivers for them :S
I tried to downgrade the kernel to 2-6-28-13 but the problem seems to be related to an other package (hal maybe)
What could be the problem here?

Edit:

My dmesg | tail output:

```
[  158.403412] usb 4-1: new full speed USB device using ohci_hcd and address 5
[  163.424903] usb 4-1: device descriptor read/8, error -110
[  168.544343] usb 4-1: device descriptor read/8, error -110
[  168.648538] hub 4-0:1.0: unable to enumerate USB device on port 1
[  168.952535] usb 4-2: new low speed USB device using ohci_hcd and address 6
[  169.167165] usb 4-2: configuration #1 chosen from 1 choice
[  169.183079] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input5
[  169.220160] generic-usb 0003:046D:C313.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:04.0-2/input0
[  169.246125] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.1/input/input6
[  169.284978] generic-usb 0003:046D:C313.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:04.0-2/input1
```

What the heck is that BTC Multimedia keyboard!? Is it a hong-kong based keyboard mafia? My usb keyboard is a logitech! Something is very wrong here...

---

### Post by barisurum on 2009-08-04
Nevermind the problem solved itself after a while

---

