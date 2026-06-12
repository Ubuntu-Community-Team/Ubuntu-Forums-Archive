---
title: "Why SATA drives are configured with a specific UDMA?"
date: 2015-03-27
forum: Hardware
---

### Post by negora on 2015-03-27
Hello:

Checking the output of the command "dmesg", I've found some entries such as these ones:

```

[    5.843784] ata2.00: configured for UDMA/100
[    5.848060] ata4.00: configured for UDMA/100
[    5.855392] ata3.00: configured for UDMA/133
[    5.858586] ata1.00: configured for UDMA/133

```

If I'm right, UDMA was the group of the modes that were available in the IDE/ATA/PATA interface to transmit the data. However, all my drivers are SATA. Then, Why does Linux set these modes? Is it to keep a backwards compatibility with some type of software or hardware? I've benchmarked the speed of my drives and all them reach the expected ones, so it seems not to have any effect in the speed of the buses.

Thank you.

---

### Post by dino99 on 2015-03-27
glance at your bios; maybe it is too old to know about actual sata devices; or the mobo chipset(s) are themselves so old

---

### Post by negora on 2015-03-27
First of all, thank you for your prompt answer ;) . 

I'm using a relatively modern mother board, an [ASUS M5A97 EVO R2.0.]("http://www.asus.com/Motherboards/M5A97_EVO_R20/"). The SATA ports are configured in AHCI mode. If I'm right, I'm booting it in legacy BIOS mode. But, even so, I think that it's has nothing to do with this issue, because even many "old" BIOS support SATA ports properly. Indeed, my previous mother board, an ASUS P5B Deluxe, worked fine with them. It's only that I never realized about these entires in "dmesg". Maybe they were there too when I used the P5B Deluxe. I'm not sure.

Do you have these entries or similar ones in your output of "dmesg"?

Thank you.

---

### Post by Yellow Pasque on 2015-03-27
Ignore the UDMA mesages [http://knowledge.seagate.com/articles/en_US/FAQ/184991en?language=en_US](http://knowledge.seagate.com/articles/en_US/FAQ/184991en?language=en_US)
(Yes, I've had them on every Linux install I used.)

---

### Post by ajgreeny on 2015-03-27
I certainly have similar entries on my system with an ASUS P8H61-MX USB3/SI: uATX, USB 3.0, SATA 3.0Gb/s mobo which is quite new.  All works as it should.

---

### Post by negora on 2015-03-27
> **Temüjin said:**
> Ignore the UDMA mesages [http://knowledge.seagate.com/articles/en_US/FAQ/184991en?language=en_US](http://knowledge.seagate.com/articles/en_US/FAQ/184991en?language=en_US)
(Yes, I've had them on every Linux install I used.)

That's an interesting article. Although they say that it's merely cosmetic, I guess that it's something done on purpose to prevent compatibility issues with old software. But that's just my supposition. Thank you for the clarification ;) .

[quote= ajgreeny]I certainly have similar entries on my system with an ASUS P8H61-MX USB3/SI: uATX, USB 3.0, SATA 3.0Gb/s mobo which is quite new. All works as it should.[/quote]

OK. Luckily it's not something bad. Thank you :).

---

