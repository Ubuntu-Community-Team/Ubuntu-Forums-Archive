---
title: "Asus UL30 and Mic quality"
date: 2010-06-02
forum: Hardware
---

### Post by loko on 2010-06-02
Hello you ul30-owners

i own one myself (ul30a). my mic is really bad. in fact, it's almost unusable to record any voice. there is a very bad noise all the time while recording.
It's also happening with Windows 7, so it could be that the mic is bad in gerneral - or it is broken.

is somebody experiencing the same problem or is my mic just broken?

---

### Post by lidex on 2010-06-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

