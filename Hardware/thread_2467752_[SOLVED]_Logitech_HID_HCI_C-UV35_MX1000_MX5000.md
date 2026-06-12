---
title: "[SOLVED] Logitech HID HCI C-UV35 MX1000 MX5000"
date: 2021-10-07
forum: Hardware
---

### Post by axelmasok on 2021-10-07
Hi Team Ubuntu,

Reviving a spare USB dongle and mouse from a decade ago.
I've spent some hours on this and finally lucked a silly easy solution I better document for the world.
There is virtually nothing documented for the most basic need I have - plug in the USB and use the mouse (in HID USB mode)

The USB Bluetooth dongle/receiver/transmitter and the mouse work fine in HCI mode and you can pair them with each other and other devices all day long, great wow.  BTW, if you can't use the Logitech C-UV35 in HCI mode to pair bluetooth devices I know you have to hold the little red button down and insert into the PC.  There are Internet search results and forums to help there.

What I want to do is walk around with the USB dongle and plug it into a number of laptops and I don't want to pair them together each time. Nor do I want to copy the keys around to each laptop. I just want to plug it in and use the mouse.  HID mode basically.  There is a whole long article on the Internet on how HID Vs HCI works.
Problem is it used to just work, then somewhere after Ubuntu 14.4 (or after), it stopped working.

Here are the devices (lsusb):

```
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 012: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 001 Device 011: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 001 Device 010: ID 046d:0b02 Logitech, Inc. C-UV35 [Bluetooth Mini-Receiver] (HID proxy mode)
```

To cut to the chase, there is a udev rule that calls hid2hci. When this runs it stops the mouse from working. 
To fix simply comment out the two lines for logitech OR add --mode=hid to the hid2hci command

/lib/udev/rules.d/97-hid2hci.rules 

```
# Logitech devices
#comment out# KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
#comment out#   RUN+="hid2hci --method=logitech-hid --devpath=%p"
# Logitech, Inc. diNovo Edge Keyboard
KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c714", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```

OR

```
# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
  RUN+="hid2hci --mode=hid --method=logitech-hid --devpath=%p"
# Logitech, Inc. diNovo Edge Keyboard
KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c714", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```

You are more than welcome to read up on what those lines are for.  If you require the C-UV35 adapter to be used for pairing bluetooth devices (HCI mode), you may need these two lines.
I worked out the problem when I plugged in the dongle and kept moving the mouse the cursor would actually move for 1/2 second then stop. So there ws something post detection that stopped it from working. Looking at the kernel logs I saw reference to udev and hid2hci.  Found the udev rule and here we are. I also booted an old 14.4 DVD and found the mouse worked immediately with no work around. Something changed software wise.

Hope that helps someone in the future. May also work for other dongles and mice, most likely NOT the Logitech Unify versions.  Basically older bluetooth stuff.

---

