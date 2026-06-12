---
title: "grub(?) won't load after installing wireless nic"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by sprice on 2007-04-30
newb here. just made the switch about three days ago and loving it.

After installing a D-Link DWL-G520revb card, as soon as I choose which OS to load in grub the comp hangs at:
```

kernal alive
kernal direct mapping tables up to 100000000 @ 8000-d000
```

---

### Post by sprice on 2007-04-30
I edited /boot/grub/menu.lst and changed 'quiet splash' to 'noapic' as I had read about that in a few other places. 

Problem fixed.

---

