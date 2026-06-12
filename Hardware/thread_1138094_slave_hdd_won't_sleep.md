---
title: "slave hdd won't sleep"
date: 2009-04-26
forum: Hardware
---

### Post by LightB on 2009-04-26
I usually spin a slave drive down with 'hdparm -y /dev/xxx' 
now on 9.04 it's spinning back up right after that command and this is printed

```
[ xxxx.xxxxxx] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6

[ xxxx.xxxxxx] ata6.00: waking up from sleep
```

with x being different numbers each time.

The drive is noisy but I'd rather not remove it. Someone have a clue what's going on?

---

