---
title: "PCI BIOS Bug 31"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by IanVaughan on 2009-09-30
During the boot process I get ```
"<timestamp> PCI: BIOS Bug #[000000031] found" 
``` (or words to that effect)

I think my harddisk is failing, is this related?

---

### Post by rreese6 on 2009-09-30
Post the output of this command:
```
sudo dmesg | grep bug -n10

```.
This may be related to you having the "PNP (Plug and Play) OS"
in BIOS enabled, If the PNP is enabled, disable it.
also post this command
```
lspci
```

Is this a compaq computer or an Intel Motherboard?

---

