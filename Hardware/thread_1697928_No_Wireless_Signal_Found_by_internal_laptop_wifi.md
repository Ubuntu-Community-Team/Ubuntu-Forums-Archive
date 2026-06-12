---
title: "No Wireless Signal Found by internal laptop wifi"
date: 2011-03-01
forum: Hardware
---

### Post by samMD on 2011-03-01
I have a HP G70-4600US Laptop and after I had installed ubuntu i can get a ethernet connection but the laptop is unable to get any sort of wifi signal just gives the status of "disconnected". I also tried using my novice experience in engaging the proprietary driver search in ubuntu but to no avail the program could not detect any additional drivers needed..

Help!

---

### Post by coffeecat on 2011-03-01
Let's see what wireless device you have. Without that it will be impossible to troubleshoot.

Post the terminal output of:

```
lspci | grep -i wireless
```If that doesn't reveal anything, try:

```
lspci | grep 802.11
```

---

