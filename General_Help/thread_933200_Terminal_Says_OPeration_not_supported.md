---
title: "Terminal Says OPeration not supported"
date: 2008-09-29
forum: General Help
---

### Post by ehsensiraj on 2008-09-29
I recently installed ubuntu on winXp. I am trying to install Huwei ETS 2051 (CDMA Wireless). When I enter "dmesg -c" in terminal I always get the message "Operation not supported". Can you please tell me why its happening.

---

### Post by sisco311 on 2008-09-29
try:
```
sudo dmesg -c
```

---

### Post by kpkeerthi on 2008-09-29
Try without the -c switch:
```
dmesg | less
```
Press <space> to scroll forward and 'b' to scroll backward.

---

