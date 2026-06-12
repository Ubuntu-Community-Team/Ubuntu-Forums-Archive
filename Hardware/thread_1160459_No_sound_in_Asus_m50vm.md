---
title: "No sound in Asus m50vm"
date: 2009-05-15
forum: Hardware
---

### Post by been_1990 on 2009-05-15
Im using Ubuntu 9.04 with a Asus M50VM series. And I cant find my sound card, I get this error message when I run aplay -l:
```
aplay: device_list:217: no soundcards found...

```
When I run Driver Status: snd_hda_intel is not active:
```
28: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.1_A02mjACiD
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x1893 
  Revision: 0x03
  Memory Range: 0xf9ff8000-0xf9ffbfff (rw,non-prefetchable)
  IRQ: 4 (no events)
  Module Alias: "pci:v00008086d0000293Esv00001043sd00001893bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Any help?

---

### Post by been_1990 on 2009-05-18
So....  Anyone?

---

### Post by been_1990 on 2009-06-07
If no one can help, please close this thread.

---

### Post by aldebaranomega on 2009-08-26
Hi,

Could u solve ur problem? I did the Ubuntu 9.04 update two days ago and
still havent found a way to make my sound working. I tried almost everthing I could find in the forums.

aplay -l:

aplay: device_list:217: no soundcards found...


lspci:

ler #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Help...

---

