---
title: "No buttery detected after suspend"
date: 2010-01-04
forum: Hardware
---

### Post by taamir on 2010-01-04
After suspend I get no warning about low battery and finaly my laptop just shuts down, I use HP Pavilion DV4.
I understand that this is a known problem - where can I get updated about it? and, is there a way around it?

BEFORE:
```
tamir@tamir-laptop:~$ cat /proc/acpi/battery/*/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4541 mAh
present voltage:         12546 mV

```

AFTER ;
```
tamir@tamir-laptop:~$ cat /proc/acpi/battery/*/state
present:                 no

```

---

### Post by taamir on 2010-01-07
BUMP 
Please Help..

---

