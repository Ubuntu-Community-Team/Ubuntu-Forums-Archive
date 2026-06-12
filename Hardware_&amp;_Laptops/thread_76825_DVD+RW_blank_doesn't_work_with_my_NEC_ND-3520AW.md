---
title: "DVD+RW blank doesn't work with my NEC ND-3520AW"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by pmjdebruijn on 2005-10-15
When trying to blank a DVD+RW with GnomeBaker using my NEC ND-3520AW DVD Recorder, it failed. It seems GnomeBaker uses dvd+rw-format to do the actual work, now starting dvd+rw-format from the console gives this:

```
pmjdebruijn@agamemnon:~$ sudo dvd+rw-format -force -blank=full -ssa=default /dev/hdc
Password:
* DVD\uffffRW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
:-[ READ FORMAT CAPACITIES failed with SK=2h/ASC=04h/ACQ=08h]: Resource temporarily unavailable
```

I'm using NEC's latest firmware...

Anybody a clue what this might mean? And how I can fix this?

Thanks in advance,
Pascal de Bruijn

---

