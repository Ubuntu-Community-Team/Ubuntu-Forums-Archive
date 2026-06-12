---
title: "[SOLVED] Random locking up"
date: 2008-11-15
forum: General Help
---

### Post by Trzone on 2008-11-15
This has been happening to me recently, for some random reason, the computer will get slower and slower, no matter what application im using.
However this time i was using firefox on yahoo mail, and slowly my mouse began to become slower moving, i thought it was firefox, but it just slowly began to freeze, the entire system.  So i had to do a hard reset after i realized that the keyboard was not responding (num lock was staying on even after i had pressed it to turn it off).  
So my question is, how do i figure out what caused it?

It could have been firefox, but how do i figure out for sure?
Specs :
OS Hardy Heron (8.04.1)
Ram: 512MB
Swap was not active at the time
AMD Athlon 1600+ (1.4GHZ)
Any help would be great

---

### Post by taurus on 2008-11-15
When you said "Swap was not active at the time", do you mean it was not used by the system or it was not mounted?

```
free
cat /etc/fstab
```

---

### Post by Trzone on 2008-11-15
The swap partition was unmounted during the time

---

### Post by Trzone on 2008-11-18
Developer versions are unstable

---

