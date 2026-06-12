---
title: "are this numbers really normal?"
date: 2008-11-09
forum: General Help
---

### Post by ieBrazil on 2008-11-09
isaque@isaque-laptop:~$ df
Sist. Arq.           1K-blocos      Usad Dispon.   Uso% Montado em
/dev/sda2             35894848   4631632  29439840  14% /
varrun                  253020        96    252924   1% /var/run
varlock                 253020         0    253020   0% /var/lock
udev                    253020        48    252972   1% /dev
devshm                  253020        24    252996   1% /dev/shm
lrm                     253020     39780    213240  16% /lib/modules/2.6.24-21-g

I used (first time) df command and found it abolve.

Where we read "Usad" you'll see Used and  "Dispon", Avail.

I just realized that I have more used than available space! How come!?! If I have a few files on my Ubuntu partition (I have dual boot)?

Is sth wrong?

Tnx!

---

### Post by Ryadt on 2008-11-09
Use ```
df -h
``` to increase readability.

---

### Post by sisco311 on 2008-11-09
run the command with the -h flag to  print sizes in human readable format (e.g., 1K 234M 2G):
```
df -h
```

[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.0G  2.3G  6.3G  27% /
[/HTML]

---

### Post by ieBrazil on 2008-11-09
Sist. Arq.            Tam   Usad Disp  Uso% Montado em
/dev/sda2              35G  4,5G   29G  14% /
varrun                248M   96K  247M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   48K  248M   1% /dev
devshm                248M   24K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-21-generic/volatile

---

### Post by sisco311 on 2008-11-09
total size of the partition: 35G
used: 4,5G
available:29G

looks ok.

---

