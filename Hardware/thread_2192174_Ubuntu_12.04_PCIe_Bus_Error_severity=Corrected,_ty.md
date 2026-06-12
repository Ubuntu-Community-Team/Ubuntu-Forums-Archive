---
title: "Ubuntu 12.04 PCIe Bus Error: severity=Corrected, type=Data Link Layer"
date: 2013-12-06
forum: Hardware
---

### Post by downingaustin on 2013-12-06
Ubuntu forums,

I have millions of these errors in my log files, as far as I can tell constantly filling it. Whenever I write to my RAID array.

```
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793628] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e4(Transmitter ID)
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793629] pcieport 0000:00:1c.4:   device [8086:8c18] error status/mask=00001000/00002000
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793630] pcieport 0000:00:1c.4:    [12] Replay Timer Timeout  
```

Also at some point when running my Veeam Backups to this server my server will hard crash and the last thing in my log is repeated.

```
NULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNUL
```

What is causing these issues and more importantly how can I correct them?

System specs.

OS: Ubuntu 12.04
Motherboard: SuperMicro X10SLH-F-O
Processor: Intel Core i3-4130
Boot Drive: Plextor M5P 128GB
Memory: 4 x Crucial 8GB ECC Memory [CT8G3ERSLD8160B]("http://www.neweggbusiness.com/product/product.aspx?item=9b-20-148-642")
PSU: Rosewill 450w
SATA Controllers: 3 x SY-PEX40008 PCI-E 2.0
Storage 12 x WD 2TB RED Drives in Linux RAID 6

My Linux knowledge is moderate to low so I am looking to the community and its expertise to help me with this.

---

