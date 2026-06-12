---
title: "Bluetooth hedset problem on Dell inspiron 1525"
date: 2008-12-21
forum: Hardware
---

### Post by Kcrsh10 on 2008-12-21
I am trying to pair my sony DR_BT21G Bluetooth headphones. I can get them to pair through Bluez, and Alsa mixer recognises them.

$ sudo cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1

 Despite this Bluez doest show them as an audio device and only allows me to transfer data files (this is,of course,not possible!) 

Can anybody offer any suggestions as to how I can resolve this?

---

