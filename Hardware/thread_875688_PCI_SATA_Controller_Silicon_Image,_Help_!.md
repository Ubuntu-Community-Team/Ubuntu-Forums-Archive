---
title: "PCI SATA Controller Silicon Image, Help !"
date: 2008-07-31
forum: Hardware
---

### Post by mr_piouf on 2008-07-31
Hi, 

I just bought a pci card to which I can plug two SATA disks, because I didn't have enough sata ports on my mother board. This SATA controller card is using a Silicon Image Chip SATALINK SIL3512.

- First is there a way to make sure that the system sees this card even if it doesnt have the right drivers yet ? I tried lspci but I dont see it. I want to make sure its not an hardware problem.

- After a few hours of google I found out that I can use the sata_sil module that supports the 3512. I used "modprobe sata_sil", nothing appends.

I dont know what to try next :( help !

---

### Post by markbuntu on 2008-07-31
Try the card in a different slot. I had a problem with my SIIG SATA PCI card so I tried a different slot and it worked.

---

