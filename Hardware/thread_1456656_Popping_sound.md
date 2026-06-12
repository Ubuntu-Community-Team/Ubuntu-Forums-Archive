---
title: "Popping sound"
date: 2010-04-17
forum: Hardware
---

### Post by WeWillow on 2010-04-17
Greetings,
 This is my first posting, as I just installed last night for the first time on this vista runing machine.  My issue is this little crackling, popping:popcorn:sound that keeps happening, regardless of muting.  Is there a sound card update or driver or something I can do?  Thanks for any suggestions,
We

---

### Post by lidex on 2010-04-18
Welcome to the forums. Can you post the output of these terminal commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

