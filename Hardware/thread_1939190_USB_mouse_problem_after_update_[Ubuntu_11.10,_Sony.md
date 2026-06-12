---
title: "USB mouse problem after update [Ubuntu 11.10, Sony Laptop]"
date: 2012-03-11
forum: Hardware
---

### Post by captainsvejk on 2012-03-11
I recently did a ubuntu update on my Sony Vaio laptop (VGN-SZ460N) and now the usb mouse has stopped working. If I plug it in, it works for a second or two and then freezes.

I'm using Ubuntu 11.10 and the last update took me to version 3.0.0.16.19 of the linux kernel.

lsusb gives this output (with usb mouse not working):

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 054c:0281 Sony Corp.
Bus 001 Device 005: ID 05ca:1835 Ricoh Co., Ltd Visual Communication Camera VGP-VCC5 [R5U870]
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 003: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem

And this in the brief window of functionality:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 054c:0281 Sony Corp.
Bus 001 Device 005: ID 05ca:1835 Ricoh Co., Ltd Visual Communication Camera VGP-VCC5 [R5U870]
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 003: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 002 Device 035: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse



Any thoughts or suggestions? I've tried booting with older versions of the kernel but it doesn't seem to make any difference.

Thanks in advance,
Svejk.

---

### Post by troymius on 2012-03-11
Hi Good Soldier Svejk. Do other devices work fine? I recently had the same problem and it ended up being a broken motherboard. Cau!

---

### Post by captainsvejk on 2012-03-11
The problem seems to be generally with the usb ports but I guess I should try booting from a cd to see if they still work in general.

I do get some functionality (intermittent use with momentary freezes) if i plug in a usb extension lead in one port and the mouse in the other, which suggests to me that it's probably some sort of conflict rather than a fundamental failure.

Sorry to hear about the motherboard though.. :)

Svejk.

---

### Post by captainsvejk on 2012-03-11
I booted with an 11.04 cd I had lying around and the usb mouse works fine with that, so that rules out a hardware failure.

---

### Post by troymius on 2012-03-12
Phew! The new LTS Ubuntu is just around the corner... I would just wait for that rather than trying to fix 11.10.

---

