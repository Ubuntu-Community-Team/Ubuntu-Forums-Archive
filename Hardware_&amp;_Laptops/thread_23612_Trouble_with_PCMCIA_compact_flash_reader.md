---
title: "Trouble with PCMCIA compact flash reader"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by jasplund on 2005-04-03
I can't get my PCMCIA compact flash reader to work. It worked perfectly in warty. The PCMCIA port works since I have no problem with me wlan-card. I've tried to boot with the reader and then remove in at put it back in. I've also tried to boot without it and the put it in. I've tried with and without my wlan-card inserted. Any suggestions?


Johan

---

### Post by az on 2005-04-03
Add to this bug immediately.  It may be fixed for Hoary's release.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by jasplund on 2005-04-04
btw "dmesg" tells me this 

"Probing IDE interface ide2...
hde: SanDisk SDCFH-256, CFA DISK drive
ide2 at 0x140-0x147,0x14e on irq 11
hde: max request size: 128KiB
hde: 501760 sectors (256 MB) w/1KiB Cache, CHS=980/16/32
hde: cache flushes not supported
 /dev/ide/host2/bus0/target0/lun0: p1
ide-cs: hde: Vcc = 3.3, Vpp = 0.0"

---

