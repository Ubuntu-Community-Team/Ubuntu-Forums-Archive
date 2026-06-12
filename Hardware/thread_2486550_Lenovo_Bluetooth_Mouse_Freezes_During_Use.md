---
title: "Lenovo Bluetooth Mouse Freezes During Use"
date: 2023-05-04
forum: Hardware
---

### Post by steevven12 on 2023-05-04
Help! I bought my wife the mouse of her dreams, and it doesn't work correctly. It pairs without any issue and never disconnects, but at some point during use (after 5-30 minutes), it completely stops responding (while staying connected according to Blueman). If I try to disconnect and reconnect with Blueman, it fails to respond to the "disconnect" command at all, and I'm forced to reboot. Then, it works again for another 5-30 minutes before freezing.

This does not seem to be related to "idling," as it happens randomly during active use.

System details:
[LIST]
[*]Lenovo ThinkPad Bluetooth Silent Mouse 4Y50X88822 ([https://www.lenovo.com/us/en/p/accessories-and-software/keyboards-and-mice/mice/4y50x88822](https://www.lenovo.com/us/en/p/accessories-and-software/keyboards-and-mice/mice/4y50x88822)) 
[*]Lenovo ThinkPad X220 
[*]Intel Corporation Wireless 7260 (rev 73) WiFi network (and Bluetooth) card/controller 
[*]Xubuntu 22.04 
[/LIST]

Tried and failed:
[LIST]
[*]Battery replacement 
[*]Pairing manually via bluetoothctl (and disabling Blueman) 
[*]Setting UserspaceHID=true in /etc/bluetooth/input.conf 
[/LIST]

Any ideas are greatly appreciated!

---

### Post by steevven12 on 2023-05-04
More things I tried that did not work:
- Used same PC and mouse under Xubuntu 23.04 with newer Linux kernel 6.2.0-20-generic (original 22.04 kernel was 5.15.0-71-generic)
- Checked if I had TLP installed because someone said it can cause Bluetooth problems (it was not installed at all; moot point)
- Turned off PCI Express power management in system BIOS (note that this WiFi/Bluetooth combo card is in a mini PCI-e slot)
- Taped over pin 20 on the mini PCI-e card (note that I already taped over pin 51 to make Bluetooth work in the first place)

Other notes:
- Whenever the mouse freezes, suspending the computer and then waking it up immediately makes the mouse work again. Same for rebooting.

---

### Post by steevven12 on 2023-05-21
Very bizarre hack of a solution:

The mouse would never, ever play nice with the Intel 7260 card (even though Bluetooth audio with wireless speakers works great and never disconnects, btw), so we bought a TP-Link UB400 USB Bluetooth dongle ([https://www.amazon.com/TP-Link-Bluetooth-Receiver-Controllers-UB400/dp/B07V1SZCY6/](https://www.amazon.com/TP-Link-Bluetooth-Receiver-Controllers-UB400/dp/B07V1SZCY6/)), which was instantly 100% perfectly compatible with Linux and the mouse. Since dongles are ugly, we hid it INSIDE the computer with a special internal USB port adapter made specifically for the ThinkPad X220 ([https://www.aliexpress.us/item/3256802303543150.html](https://www.aliexpress.us/item/3256802303543150.html)).

Now the computer has 2 bluetooth adapters, which Blueman handles simultaneously very elegantly. You can select which devices to connect to through which adapters easily in the GUI. The mouse auto-reconnects through the correct adapter every time, and has been working seamlessly for days.

---

