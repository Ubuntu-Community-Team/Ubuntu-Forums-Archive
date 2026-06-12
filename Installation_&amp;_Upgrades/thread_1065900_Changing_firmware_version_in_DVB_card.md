---
title: "Changing firmware version in DVB card"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by cliveb on 2009-02-10
I'm running Ubuntu 8.10, and using it as the backend server for a MythTV setup. The TV tuner card is a Hauppauge Nova-TD-500. (Although it's a PCI card, it actually has a pair of USB tuners on it).

It generally works well, except that there are intermittent errors that cause recordings to fail. DMESG has entries like this:
"DiB0700 I2C write failed"
and:
"DiB0700 I2C read failed"

Over on LinuxTV.org, it is suggested that installing the latest firmware might fix problems like this, so I'd like to try that out. (The firmware installed by default in Ubuntu 8.10 is dvb-usb-dib0700-1.10.fw, while the latest is dvb-usb-dib0700-1.20.fw).

But how do I change the firmware that Ubuntu downloads to the card on boot-up?
(Note: I've never built a Linux kernel - I'm hoping it doesn't require that level of involvement).

---

