---
title: "Strange MX5000 + MX1000 Blue Tooth Behavior"
date: 2009-07-12
forum: Hardware
---

### Post by matchrocket on 2009-07-12
Installed 9.04 and when I boot up, neither my mouse or my keyboard work until I unplug the receiver and move it to a different USB port.  Then they start working.  I can put it back to the original location and it will also work until I reboot again.

Its very annoying.  hcitool scan shows nothing, neither does hcitool dev.  The only thing that shows anything is lsusb, output below:

Bus 001 Device 004: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 009: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 002 Device 008: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 002 Device 007: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 003: ID 03f0:2f11 Hewlett-Packard PSC 1200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So the devises are registered, but won't enable on first boot.  Any thoughts?

---

### Post by windy81 on 2009-07-12
i have a BT Logitech MX laser mouse (not sure what model exactly) that came with the diNovo package.

Mine seems to work fine and i run it through the Logitech BT receiver. Connects at start-up immediately.

Im in Windows at the moment, still Ubuntu noob, but if u want i can do a copy paste "sudo lsusb" for you. PM me if thats any help. or a "sudo hcitool"

---

### Post by matchrocket on 2009-07-12
After digging around a little bit more I found the following:

open a terminal, type @ Prompt  sudo gedit /etc/default/bluetooth
 You will see:
 HID2HCI_ENABLED=1
HID2HCI_UNDO=1
 Change it to:
 HID2HCI_ENABLED=0
HID2HCI_UNDO=1


This DOES work. Why? I am not sure. when I find out, I will post it here.


:guitar:

---

