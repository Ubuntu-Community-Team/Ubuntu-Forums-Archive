---
title: "No laptop sound"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by HokeyFry on 2006-01-09
I installed ubuntu hoary on my laptop some time ago (recently upgraded to breezy) and have searched how to get the sound to work on it, but to no avail. Can someone help me?

Here is some info about my laptop (it's old, so you know):

[LIST]
[*]Dell Latitude CPi
[*]Processor: Pentium II (Deschutes)
[*]RAM: 128 MB
[*]4 GB (1.5 GB left)
[/LIST]

I know you probably need the sound card, but when I run "sudo lshw -businfo" I don't see it come up, so I probably need help finding the make first. And if the card simply didn't install when I installed hoary, I will need to know how to install it once I find the make.

Thanks in advance for the help!

---

### Post by HokeyFry on 2006-01-10
I ran dmesg and could not find anything on sound anywhere, so I definitely think that the sound card was not installed (may be mistaken, correct me if I am wrong). Any way I can install it?

---

### Post by Amon_Re on 2006-01-10
[QUOTE=HokeyFry]I ran dmesg and could not find anything on sound anywhere, so I definitely think that the sound card was not installed (may be mistaken, correct me if I am wrong). Any way I can install it?[/QUOTE]

Can you post the output of **sudo lspci** ?

---

### Post by HokeyFry on 2006-02-06
here is the output to "sudo lspci"

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph] 128XD] (rev 01)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:01:00.0 Network Controller: Broadcom Corporation: Unknown device 4318 (rev 02)
```

---

### Post by rmestre on 2006-04-30
did you ever figure out what to do because I am having the same problem

---

