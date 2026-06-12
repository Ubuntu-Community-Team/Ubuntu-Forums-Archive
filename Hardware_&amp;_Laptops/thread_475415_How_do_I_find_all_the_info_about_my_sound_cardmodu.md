---
title: "How do I find all the info about my sound card/module/chipset//driver?"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by matheuu on 2007-06-16
Question says it all!
Cheers if you can help.

---

### Post by FuturePast on 2007-06-16
```
$ lspci
```

and have a look around /proc/asound

---

### Post by matheuu on 2007-06-16
Thanks
couldn't find any /proc/asound....did find

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


what would this be? the card, chip, module or the driver?

---

### Post by FuturePast on 2007-06-16
This is the Intel chipset that you have on your motherboard.

Did you try?:```
$ ls /proc/asound/
card0  cards  devices  Intel  modules  oss  pcm  seq  timers  version
$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 20

```

---

