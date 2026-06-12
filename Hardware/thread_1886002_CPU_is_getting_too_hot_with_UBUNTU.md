---
title: "CPU is getting too hot with UBUNTU"
date: 2011-11-24
forum: Hardware
---

### Post by mauro leonelli on 2011-11-24
Hi, I have a brand new Dell Vostro with windows 7 and Ubuntu11.10. Everything is working perfectly, but the CPU is getting too hot when I'm using Ubuntu. Is there any incompatibility?
Thanks!
Mauro

---

### Post by BC59 on 2011-11-24
First of all you have to install the video proprietary drivers.

Then if you are not satisfied, you can install Jupiter:

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

Then execute Jupiter from dash and you will have all the options to tweak the temperature.

---

### Post by mauro leonelli on 2011-11-24
Perfect! The temp is normal now. But the desktop appearance has changed. Is this normal? 
Thank you very much!

---

### Post by BC59 on 2011-11-24
If you installed the proprietary driver then your video card is working at 100% of it's capabilities, so that's why you noticed a difference.

---

