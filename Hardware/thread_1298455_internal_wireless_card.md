---
title: "internal wireless card"
date: 2009-10-22
forum: Hardware
---

### Post by ninetailedfox on 2009-10-22
I just installed ubuntu like 1 hour ago and cant get my internal wireless card to work the button is on but no light where the wireless icon is. How do i get it to work?

---

### Post by Dark_Stang on 2009-10-22
What kind of wireless card is it? If you're not sure post the output of...
```
lspci | grep -i "wlan"
```

---

### Post by ninetailedfox on 2009-10-23
i have an atheros and thats all i know the code u gave me didnt do anything

---

### Post by IcarusR on 2009-10-23
Try this...
```
lspci | grep Network
```
It should give model & rev.

---

### Post by chirranth on 2009-10-23
even I have the same problem..

Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by ninetailedfox on 2009-10-23
thank it worked i have the same thing as chirranth i have a 
Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01

---

### Post by Dark_Stang on 2009-10-23
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

---

