---
title: "How can I tell which SATA Revision my Laptop Motherboard Supports?"
date: 2017-01-10
forum: Hardware
---

### Post by saltytaro2 on 2017-01-10
[COLOR=#000000][FONT=arial]I am planning on installing an SSD in my Acer Aspire E5-511 C7X7 ([https://www.acer.com/ac/en/GB/cont](https://www.acer.com/ac/en/GB/cont)[/FONT][/COLOR][COLOR=#000000][FONT=arial]ent/model/NX.MPKEK.022) by replacing the 9.5mm optical drive with this hard drive caddy ([http://www.ebay.com/itm/3213948563](http://www.ebay.com/itm/3213948563)[/FONT][/COLOR][COLOR=#000000][FONT=arial]66) but I am unsure if it will be worth the money since I do not know if the motherboard supports SATA I, II, or III. How can I check this?[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]I am running Kubuntu 16.10 and hardinfo tells me that my primary HDD that was stock included in the laptop is the Western Digital ATA WDC WD10JPVX-22J 1TB HDD ([http://www.datamemorysystems.com/p](http://www.datamemorysystems.com/p)[/FONT][/COLOR][COLOR=#000000][FONT=arial]sds41153/). The HDD itself is specified to have the SATA 6 Gb/s interface, from which I understand to be SATA III.[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]dmesg in the console tells me that my two SATA controllers link up to 1.5Gbps and 3.0Gbps. I assume the first is my optical drive and the second is my HDD. This is leading me to believe that my HDD is SATA II and my optical drive is SATA I. Is this information correct?[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]I would assume that Acer wouldn't ship a SATA III HDD on a laptop whose motherboard supports anything less than that. Am I safe on this assumption? And is it possible that my HDD and optical drive use a different SATA interface? I assume they use the same one and I hope it is SATA III compatible, but again, I want to be sure.[/FONT][/COLOR]

---

### Post by efflandt on 2017-01-10
```
$ grep "Gbps" /var/log/syslog
Jan  9 18:04:06 XPS-8100-1404 kernel: [    0.671908] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x2f impl RAID mode
Jan  9 18:04:06 XPS-8100-1404 kernel: [    1.024171] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  9 18:04:06 XPS-8100-1404 kernel: [    1.368367] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  9 18:04:06 XPS-8100-1404 kernel: [    1.688558] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
```1.5 Gbps is SATA1 (my CD/DVD drive), 3.0 Gbps is SATA2, 6.0 Gbps is SATA3. In this case the SSD on ata2 is capable of SATA3, but the PC is only capable of SATA2.

Or if you have not rebooted in a very long time it might be in one of the other syslog.# files, or reboot and then it would be in syslog.

---

### Post by kpatz on 2017-01-10
> **efflandt said:**
> Or if you have not rebooted in a very long time it might be in one of the other syslog.# files, or reboot and then it would be in syslog.dmesg should have it:```
dmesg | grep Gbps
```

---

### Post by Yellow Pasque on 2017-01-10
It's a Braswell chip, so it really should support SATA 6Gbps.

> I would assume that Acer wouldn't ship a SATA III HDD on a laptop whose motherboard supports anything less than that. Am I safe on this assumption?
No, they're backwards compatible. Plus, SATA 6Gpbs isn't significantly faster for mechanical hard disks, especially a 5400RPM laptop hard disk.

---

