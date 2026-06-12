---
title: "need help patching ath5k driver."
date: 2009-08-01
forum: Hardware
---

### Post by w_1_n_d on 2009-08-01
Hello i download rtl8187_2.6.24v3.patch and ath5k-injection-2.6.27-rc2.patch. when i try to install the patching using this command patch -np0 ath5k-injection-2.6.27-rc2.patch. It sends me a message saying theres nothing but garbage... :confused::confused::confused::confused:
patch -np0 -i rtl8187_2.6.24v3.patch 
patch: **** Only garbage was found in the patch input. i copied and pasted the error message. Thank you to all in advance that took the time to read and reply to this.:KS:KS:KS:KS

---

### Post by albanodesign on 2009-08-01
if u are using airckrack there no need for patching
there all included i mean the last aircrack
u nedd only do $ sudo airmon start wlano

change the wlano to your own device seems atho

than u will be able to inject

ive tryed 3 cards and it works well no need for patching

---

### Post by albanodesign on 2009-08-01
sorry airckrack-ng
and $ airmon-ng start wlan0

---

### Post by w_1_n_d on 2009-08-01
Does the atheros 5006ex pci express card need patching? from what i read, i dont think it does. But i a web page i read said if u patch it with a certain patch you get improvements. So what do you think? thx for ur time and effort! i rellay aprreciate it.

---

### Post by albanodesign on 2009-08-12
me to read some pages but wen i tryed to do injection i realised that i didnt need patching and as i read atheros is the best supported for injection

---

### Post by w_1_n_d on 2009-08-19
Yep thats right, my card can use injection. yaaaaaaaaaaaaaaaaa.:lolflag::lolflag: :guitar::guitar::guitar:\\:D/\\:D/

---

