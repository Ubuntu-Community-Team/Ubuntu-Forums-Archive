---
title: "RAM improperly reported&amp;used"
date: 2008-09-16
forum: Hardware
---

### Post by helwitch on 2008-09-16
Running kubuntu 8.04, and it's not properly reporting my RAM installed, and presumably misreporting the RAM used. When I run lshw, it shows two sticks of RAM, each 2GiB. However, in system guard, it shows about 2.5GB or so of RAM, not the 4GB it should. This RAM used to work fine. My laptop got a new motherboard however (factory repair for AC port problem), and when I swapped the factory RAM back to the 4GB of RAM, I noticed this happening. I've swapped the sticks around, and run them individually, each stick seems to be working fine in and of itself.
[IMG]http://pics.livejournal.com/heldc/pic/00073xda[/IMG][IMG]http://pics.livejournal.com/heldc/pic/00074p34[/IMG]

---

### Post by IntuitiveNipple on 2008-09-16
Let's see what the kernel discovers during start-up.

Please attach a (compressed) copy of /var/log/dmesg:
```

cd ~
cat /var/log/dmesg | gzip > dmesg.log.gz

```

---

### Post by helwitch on 2008-10-30
Sorry it took me so long to get back with this. I had to get a new hard drive for the laptop cos the old one died, and then it was midterms.

---

