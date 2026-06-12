---
title: "Ubuntu 16.0.4 - Dual Gigabit - Intel 82575 interface, one side active"
date: 2018-08-30
forum: Hardware
---

### Post by securitydad on 2018-08-30
I am trying to understand why my Intel 82575-T2 interface card is not supporting both of the interfaces being active at the same time.  This is actually the second card I purchased for the desktop, and I do not understand why it is not functioning as expected.  Here is the information:

02:00.0 Ethernet controller: Intel Corporation 82575EB Gigabit Network Connection (rev 02)
02:00.1 Ethernet controller: Intel Corporation 82575EB Gigabit Network Connection (rev 02)


ethtool -i enp2s0f1
driver: igb
version: 5.4.0-k
firmware-version: 1.115, 0x87850000
expansion-rom-version: 
bus-info: 0000:02:00.1
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: yes

Any suggestions where to trouble shoot would be appreciated.  Thank you.

---

### Post by TheFu on 2018-08-30
What do you expect?
Is the correct driver loaded?
How are each interfaces configured?  [https://github.com/brandt/intel-igb](https://github.com/brandt/intel-igb) has examples, but older code, so I'd stick with the examples as a start.

---

### Post by securitydad on 2018-08-31
Actually, I thought that the Driver in Ubuntu would be correct already.  How many people already use Ubuntu and have Intel Gigabit PCI interfaces?  Probably a lot.

The Drive loaded appears to be correct.  Thank you.

---

### Post by securitydad on 2018-08-31
In fact, the drive I am displaying as being loaded, is newer than what is on Github.

---

### Post by TheFu on 2018-08-31
> **securitydad said:**
> In fact, the drive I am displaying as being loaded, is newer than what is on Github.

The README file on github has settings/options to make the driver behave in a way you might like. Did that not work?
There is also troubleshooting information inside it.

And be certain to check the system logs.

---

### Post by securitydad on 2018-09-01
Thank you, will check again.

---

### Post by securitydad on 2018-09-01
Looks like a plethora of options exist.  Can you offer any suggestions based on the ethtool info? I just want to get both of the NICs active on the card, is this too mush to ask?

---

