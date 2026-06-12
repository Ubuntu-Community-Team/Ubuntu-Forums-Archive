---
title: "wireless mouse moves but doesn't click"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by patrikj on 2005-08-10
I just installed Ubuntu 5.04 on a HP desktop with a wireless keyboard and mouse. The keybord works fine and the mouse pointer moves, but I cannot click. With KNOPPIX from May 2005 it works fine so my question is basically what I need to do to upgrade relevant parts (the kernel?) of Ubuntu 5.04 to match the Knoppix version. If I don't find a quick fix for this I will go back to Mandriva (or try RH/Fedore) but I'd really like to try a system based on Debian.

I have done an hour of googling (with [http://www.linuxquestions.org/questions/history/170227](http://www.linuxquestions.org/questions/history/170227) as the best match) but I'd like to avoid patching the kernel myself. With KNOPPIX working it seems somebody already fixed the problem, I just need to know how to upgrade properly (using only the text console).

Thanks in advance,
  Patrik


Details: (excerpt from dmesg for ubuntu)
mice: PS/2 mouse device common for all mice

usbcore: registered new driver hiddev

usbhid: probe of 1-1:1.0 failed with error -5
usbhid: probe of 1-1:1.1 failed with error -5

usbcore: registered new driver usbhid

drivers/usb/input/hid-core.c: v2.0:USB HID core driver

input: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.0-1
input,hiddev96: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.0-1

drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found

-------------------

---

### Post by patrikj on 2005-08-26
Upgrading to the latest kernel fixed the mouse click problem, but I got some new problems (see the other post [http://ubuntuforums.org/showthread.php?t=58064)](http://ubuntuforums.org/showthread.php?t=58064)).

/Patrik

---

