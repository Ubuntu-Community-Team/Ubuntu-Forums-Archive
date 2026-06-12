---
title: "asus rog rampage v edition 10 &quot;no w-ifi adaptor found&quot; when I set up wi-fi"
date: 2018-08-29
forum: Hardware
---

### Post by Ferule_Bezel on 2018-08-29
It's onboard wifi, enabled in bios and I just updated the bios.  

Do I need to add some propietary drivers or what?

---

### Post by Yellow Pasque on 2018-08-31
If you have a wired connection, get the wireless-info: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

If you don't have a connection, try and at least figure out what wireless chipset it's using:
```
lspci
```

Supposedly, it's some sort of Broadcom chipset, but Asus makes it difficult to figure out which one.

---

### Post by Ferule_Bezel on 2018-08-31
When I went to get the propietary drivers for my Nvidia card a Broadcom wifi card option came up as well.  I chose that and everythig got better.

---

