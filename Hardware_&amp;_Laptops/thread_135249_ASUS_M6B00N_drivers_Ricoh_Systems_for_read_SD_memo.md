---
title: "ASUS M6B00N: drivers Ricoh Systems for read SD memory + other troubles"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by soundwave on 2006-02-23
i have a laptop ASUS M6B00N and don't have controllers of Ricoh System 5C476, my ubuntu breezy 5.10 don't load /dev/sda0 or sda1, so don't mount SD memories :(
When reboot or shutdown, i could shutdown or restart my system manually with the power switch...
my laptop is incompatible with ubuntu or what??? 

thanks ;)

---

### Post by angelogladding on 2006-11-03
Hey all just following up on this old thread in regards to the same laptop running Edgy. I also have an M6N and would like to figure out how to get my SD card working. I have a feeling this one's easy. Running ```
dmesg | tail
``` outputs the following:

[17184985.456000] pcmcia: registering new device pcmcia0.0
[17185829.788000] pccard: card ejected from slot 0
[17185846.208000] pccard: PCMCIA card inserted into slot 0
[17185846.208000] pcmcia: registering new device pcmcia0.0
[17186261.028000] pccard: card ejected from slot 0
[17186267.616000] pccard: PCMCIA card inserted into slot 0
[17186267.616000] pcmcia: registering new device pcmcia0.0
[17186635.684000] pccard: card ejected from slot 0
[17186777.060000] pccard: PCMCIA card inserted into slot 0
[17186777.060000] pcmcia: registering new device pcmcia0.0

Do I have to mount it? I can't find it at /dev/sda, /dev/sdb, etc.

Kinda lost. Any help appreciated.

Thanks,
Angelo

---

### Post by soundwave on 2007-05-04
Feisty will be solution????

---

### Post by soundwave on 2007-10-11
well, don't work with Ubuntu 7.04 ¬¬

---

### Post by soundwave on 2007-11-23
i dont probe, but i believe what to run in Gutsy! :D

---

### Post by Lazy123 on 2008-04-06
I have Aopen 1557G laptop and I get the same errors in Hardy.

[108689.532143] pccard: PCMCIA card inserted into slot 0
[108689.532273] pcmcia: registering new device pcmcia0.0
[108689.532484] 0.0: GetNextTuple: No more items
[108689.532503] pata_pcmcia: probe of 0.0 failed with error -12
[108689.538799] 0.0: GetNextTuple: No more items
[108689.539363] pata_pcmcia: probe of 0.0 failed with error -12

---

