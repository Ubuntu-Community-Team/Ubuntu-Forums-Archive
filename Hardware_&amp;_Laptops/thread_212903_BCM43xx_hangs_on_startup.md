---
title: "BCM43xx hangs on startup"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by derk.d on 2006-07-10
After a fresh install in june I had everything worked, including the broadcom module. Now a month later I get everytime at the startup 2 times the keyring popup, when I fill it in 2 times(some times 3 times) the whole system freezes, I can do nothing, not even the mouse is responding, so I have to switch of the laptop by hitting the startup button.
The only solution is the following: when the system has startup I get the keyring, I don't fill in anything and only open a terminal window and hit:
```
sudo rmmod bcm43xx
```
now I typ my password, after that I hit:
```
sudo modprobe bcm43xx
```
and everything is working again...
I have it with both kernels, the first one and the new updated one, I update every day(if there is an update) also when I close my laptop it will not hybernate anymore with the new kernel and his updates. 
But the most important thing is to let my laptop funtion normal again... 
can somebody help me out?

---

### Post by derk.d on 2006-07-13
since I removed the keyring I never had this problem again so far!

---

