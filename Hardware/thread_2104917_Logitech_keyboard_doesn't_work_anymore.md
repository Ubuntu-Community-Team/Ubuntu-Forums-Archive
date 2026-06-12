---
title: "Logitech keyboard doesn't work anymore"
date: 2013-01-14
forum: Hardware
---

### Post by GammaPoint on 2013-01-14
Hi all, 

I have a Logitech S510 keyboard that has been working just fine for...basically ever (as in years). It seemed as though the batteries were getting low and so I replaced the batteries today. However, after I replaced the batteries and tried to pair it again, it wouldn't really work. 

I *think* it paired correctly (pressing the F mode button on the keyboard changes whether the 'F' on the receiver is lit up or not). However, input to the keyboard does not register to the computer. 

If I run lsusb I see the following:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard

```

The Dell keyboard is what I'm currently typing on. The Logitech Unifying Receiver is what my mouse is paired to, and the Logitech LX710 Desktop Laser is the USB connection corresponding to the receiver for the keyboard. 

Has anyone else seen anything like this? Is there something else that I can test?*

*besides trying a different computer which I'll do the next chance I get, but they are also Xubuntu machines.I'm running Xubuntu 12.04.

---

### Post by efflandt on 2013-01-15
According to the Quick Start Guide for S510, for each device separately, press the button on the receiver and then press the button "under" the device (under keyboard or mouse).

[http://www.logitech.com/repository/1408/pdf/12969.1.0.pdf](http://www.logitech.com/repository/1408/pdf/12969.1.0.pdf)

That does not mention anything about an "F" button.

---

