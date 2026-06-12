---
title: "problem with SATA controller"
date: 2008-09-26
forum: General Help
---

### Post by mio75 on 2008-09-26
Hi,

I'm a new user of ubuntu so I downloaded wubi installer and install ubuntu. I don't understand why i've to disable sata to boot
when I choose ide or raid mode ubuntu drop me in busybox. 

thanks for help !

---

### Post by russlar on 2008-09-26
:confused:

---

### Post by fjgaude on 2008-09-26
What type of drives are you using, PATA or SATA?

---

### Post by mio75 on 2008-09-27
I've sata 
now I've got another error 

ata1.00: qc timeout (cmd 0xef)
ata1.00: failed to set xfermode (err_mask=0x4)
ata1: failed to recover some devices, retrying in 5 secs
ata1.00: qc timeout (cmd 0xef)
ata1.00: failed to set xfermode (err_mask=0x4)
ata1.00: limiting speed to UDMA/33:PIO3
ata1: failed to recover some devices, retrying in 5 secs
ata1.00: qc timeout (cmd 0xef)
ata1.00: failed to set xfermode (err_mask=0x4)

---

### Post by fjgaude on 2008-09-27
Sorry, but the only thing I can think of is hardware failure, motherboard.

Ubuntu now handles all drives as sata, so I can't see how you can disable sata and still boot.

---

