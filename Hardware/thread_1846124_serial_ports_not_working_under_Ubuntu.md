---
title: "serial ports not working under Ubuntu"
date: 2011-09-18
forum: Hardware
---

### Post by daveoz66 on 2011-09-18
Seems like a linux kernel or driver issue. We have a industrial type motherboard with 4 serial ports that will not work when running arch linux; and this problem has us stumped. The ports work with windows embedded, so we know the hardware is good. The super IO chip on the MB is old enough that drivers should not be a problem. And the flow control pins work (indicate the correct voltage) when set manually through a comms tool (coolterm). However we cannot get the ports to communicate with known good serial devices (that work with other computers and with the same MB running windows embedded). Also worth noting is the same harddrive with this linux OS can be booted on a different industrial board and those serial ports work fine. Also this problem occurs under both Arch Linux and Ubuntu.
The kernel is updated and auto compiled following update. setserial returns expected IRQ and address settings for the ports (matching up with bios settings), and running setserial with autoconfigure returns the same settings. 
Only odd thing noticed is that dmesg shows two different IRQs for ttyS0 in two different lines, but the other ports do not shows up this way. All ports indicate connected when tested with coolterm, but again no data is ever transmitted or received successfully!!
Any ideas on the cause of this problem, or suggestions on how to better test are appreciated!!

---

