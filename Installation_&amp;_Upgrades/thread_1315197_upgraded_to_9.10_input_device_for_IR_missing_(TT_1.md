---
title: "upgraded to 9.10 input device for IR missing (TT 1501 DVB-C)"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by tral on 2009-11-05
Hello,
i recently updated my system from 9.04 to 9.10 most stuff seems to work fine out of the box.
but:
im using the DVB-C Card TT 1501:
```
01:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
    Subsystem: Technotrend Systemtechnik GmbH Device 101a
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at f9eff800 (32-bit, non-prefetchable) [size=512]
    Kernel driver in use: budget_ci dvb
    Kernel modules: budget-ci
```the card comes with a remote (IR) which was working fine in 9.04.
in 9.04 i was able to use the dev 
```
/dev/input/by-path/pci-0000:01:0a.0-event-ir
```wiht lirc, but the device is missing since my upgrade to 9.10.

I can't remember to have done anything special to get it working in 9.04.

Any hints?

TIA

ps: In fact it is a mythbuntu installation but i think this is a general issue so i prefixed the thread with "ubuntu", please correct me if i'm wrong here..

---

### Post by tral on 2009-11-10
no one has any ideas? Really?

---

### Post by Leolik on 2009-11-19
do
```
sudo dpkg-reconfigure initramfs-tools
```
and after that - reboot

that's may help

Sorry for my English

---

### Post by tral on 2009-11-20
> **Leolik said:**
> do
```
sudo dpkg-reconfigure initramfs-tools
```
and after that - reboot

that's may help

Sorry for my English
sadly this hasn't changed anything... do i need to load any special modules to get this work?

---

