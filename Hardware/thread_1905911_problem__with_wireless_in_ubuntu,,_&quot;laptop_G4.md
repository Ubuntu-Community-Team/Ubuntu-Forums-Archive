---
title: "problem  with wireless in ubuntu,, &quot;laptop G450&quot;"
date: 2012-01-08
forum: Hardware
---

### Post by aditya anand on 2012-01-08
I have lenovo G450 , when i install ubuntu or other linux os , i have problem with my wireless, my wireless card "BROADCOM" don't run on wlan0, it run on eth1 , due which i have to face problems in running aircrack-ng and enabling monitor mode...



       " Is there any solution to run my wireless card on wlan0 in ubuntu.." on my laptop lenovo G450

---

### Post by carl4926 on 2012-01-08
Please post the result of

```
lspci -nnk
```

What version of Ubuntu?

---

### Post by madvinegar on 2012-01-13
Do not activate any driver from the "additional drivers". If it is activated, de-activate it.

Then plug in your ethernet cable (so as to get internet), open synaptics and download and install "b43-fwcutter" and "firmware-b43-installer".

This should do the trick.

---

