---
title: "hdd does not stay in standby mode"
date: 2010-11-13
forum: Hardware
---

### Post by Freaky#Funga on 2010-11-13
Hi all. I've done this sequence of commands in order to spin down few drives which are not needed in the moment
```

# for i in b c d e ; do umount /dev/sd$i ;done
# for i in b c d e ; do hdparm -S 1 /dev/sd$i ;done
```
... <some non-error output>

When I check mount, drives are really not mounted and after 5sec I can hear them spin down. So far everything ok.

After few minutes (less than 10) all drives wake up one by one for no reason and then spin down again. What the hell is going on?

---

