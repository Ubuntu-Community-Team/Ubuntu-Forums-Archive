---
title: "Hardware Devices Command?"
date: 2010-07-10
forum: Hardware
---

### Post by brazzer30 on 2010-07-10
What command via terminal can I use to list all hardware devices connected to my machine?

---

### Post by Naitsirhc Hsem on 2010-07-10
lspci
lsusb

---

### Post by meoconvn38 on 2010-07-10
dmesg 

hope this can help

---

### Post by jocko on 2010-07-10
This is a good one:
```
sudo lshw
```
(sudo is needed to get as much info as possible...)
And to get the output in a nicely formatted html file:
```
sudo lshw -html > filename.html
```

---

