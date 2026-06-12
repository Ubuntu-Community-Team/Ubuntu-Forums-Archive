---
title: "fan noise on sony vaio problem"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by paul84 on 2008-04-03
Hello
i' have a sony vaio vgn-s5xp/n and i have a big problem with the cpu fan that produces an	
unbearable noise. The fan start running with the starting of ubuntu e never stop it.
Please help me

---

### Post by acron1 on 2008-04-03
If your laptop is more than a year old and you don't regularly clean the heatsink/fan assembly you may have an overheating problem. Try cleaning it out and see if that helps.
Good luck.

---

### Post by sysdrum on 2008-04-03
The issue is related to a heat sensor it try googling for acpi sensor linux
or run this command to check the  ```
acpi -t
```    to check the temp of the machine

---

### Post by dksdk on 2008-04-03
acron1 is right. I was annoyed with my 4 year old vaio's fan noise. I just opened the case and found that there was loads of dirt clinging to the fan and effectively minimising the amount of air that could enter the case. Cleaned it and there is a big difference in the noise, a 75% reduction. Try it if you have a more than a couple of year old lappy....:KS

---

### Post by paul84 on 2008-04-05
i' have cleaned my laptop more than one time but the problem persist.
The problem is the ACPI module that makes a bad management of the fan.
I have installed also a program called fansilencer that make the laptop silent but produce dangerous voltage fluctuation on the fan.

---

