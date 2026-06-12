---
title: "2'5&quot; SATA SSD question"
date: 2022-04-12
forum: Hardware
---

### Post by f23948 on 2022-04-12
I am using my 2'5" SATA SSD on my desktop PC, can I set to AHCI in BIOS? (NOT PCIe 3, NOT PCIe NOT NVMe NOT M.2 NGFF)ujm

---

### Post by #&amp;thj^% on 2022-04-12
I would enable AHCI, because: (I quote a superuser member)
[list]
    [*]It often boosts performance (your SSD might be an exception, but if you run a SSD and a HDD then the HDD will get some boost).
    [*]It offers additional features (e.g. hot-plugging drives).
    It is enabled just about everywhere else and having a system unexpectedly in a ancient compatibility mode would throw me for a loop. I realise this might be a personal thing.[/list]

**Reasons not to use AHCI:**
[list]
    [*]You use windows XP (now nearly 22 years old) and do not want load additional drivers during installation. (XP does not understand AHCI. It need a floppy with drivers for that).
    [*]If you have the rare situation where one specific disk is slower with AHCI. In the part you quoted it merely states that it can actually hinder performance. Not that it does, nor that it is significant. Therefor I would test with both AHCI enabled and with AHCI disabled.[/list]

Note that if you run Windows 7 (or Linux or BSD), then you can change betyween AHCI and IDE-compatible mode without reinstalling.

---

### Post by f23948 on 2022-04-12
> **1fallen said:**
> I would enable AHCI, because: (I quote a superuser member)
[LIST]
[*]It often boosts performance (your SSD might be an exception, but if you run a SSD and a HDD then the HDD will get some boost). 
[*]It offers additional features (e.g. hot-plugging drives).
    It is enabled just about everywhere else and having a system unexpectedly in a ancient compatibility mode would throw me for a loop. I realise this might be a personal thing. 
[/LIST]

**Reasons not to use AHCI:**
[LIST]
[*]You use windows XP (now nearly 22 years old) and do not want load additional drivers during installation. (XP does not understand AHCI. It need a floppy with drivers for that). 
[*]If you have the rare situation where one specific disk is slower with AHCI. In the part you quoted it merely states that it can actually hinder performance. Not that it does, nor that it is significant. Therefor I would test with both AHCI enabled and with AHCI disabled. 
[/LIST]

Note that if you run Windows 7 (or Linux or BSD), then you can change betyween AHCI and IDE-compatible mode without reinstalling.

thank you

---

