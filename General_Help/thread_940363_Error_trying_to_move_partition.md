---
title: "Error trying to move partition"
date: 2008-10-06
forum: General Help
---

### Post by rapper97 on 2008-10-06
I have used GParted in its many incarnations (as well as QtParted, which shouldn't give me any different results, right?) and always with the same result - while trying to move an ext3 further down the disk, to the "right," I keep getting an I/O error. My friend recommended [font="monospace"]cfdisk[/font], but as far as I can tell, you can't move partitions with that. Are there any alternatives to [font="monospace"]parted[/font] that can move a partition in order to make the preceding partition larger, or anything y'all can think of to make it play nice with my hard drive? Alright, thanks

```
 copia di 62615628 settori usando una dimensione blocco di 16384 settori  37:02    ( ERROR )
     	[I]copiati 51884108 su 62615628
     	Error while reading block at sector 96711081[/I]
 52179020 settori copiati
messaggi di libparted    ( INFO )
 *Input/output error during read on /dev/sda*
```

---

