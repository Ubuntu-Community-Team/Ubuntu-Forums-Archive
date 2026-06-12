---
title: "Error message when trying to read DVD"
date: 2008-08-27
forum: General Help
---

### Post by lsutiger on 2008-08-27
I am receiving the following error when trying to read a DVD:
```
mount: block device /dev/scd0 is write protected, mounting read-opnly mount: wrong fs type, bad option, bad superblock on dev/sdc0, missung codepage or helper program, or other error  In some cases useful inf is found in syslog - try dmesg | tail or so
```

I can read this disc fine in Windows.

dmesg | tail gives me:
```
brian@brian-linux:~$ dmesg | tail
[243132.388461] cdrom: This disc doesn't have any tracks I recognize!

```

Any ideas??


Even funnier - I can read it through my WinXP Virtualbox...

---

