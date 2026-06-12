---
title: "wlan on toshiba a60 help"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by blueshome on 2005-06-10
The integrated wlan card on my satellite A60 (chipset atheros) doesn't work....
better... it's not found.
I tried to found a solution in the forum, for exemple
[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=Atheros](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=Atheros)

but none.

The same thing when I try to use a wlan PC-Card that worked fine on my old toshiba with ubuntu

Can someone help me
please  O:)

---

### Post by kleeman on 2005-06-10
What does 

dmesg | grep ath

show?

---

### Post by blueshome on 2005-06-10
Nothing....
realy nothing
the same when I try whith the pci-card.

---

### Post by kleeman on 2005-06-10
OK what happens when you do

sudo modprobe ath_pci

Check the effect also using

dmesg | grep ath

again

---

### Post by blueshome on 2005-06-11
modprobe ath_pci
FATAL: Module ath_pci not found

How I can install this module

---

### Post by blueshome on 2005-06-11
Solved :grin: 
I have download the iso
with kernel 2-6-10-5 (before 2-6-10-2)
and I have install it
Now wlan woks fine

Thanks kleeman for your disponibily  :)

---

### Post by kleeman on 2005-06-11
No worries.

---

