---
title: "Help with dual boot reinstall"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2009-07-12
I am running Ubuntu 8.10 and Vista Ult.  My Vista has become infected with a nasty trojan, suprise suprise, and the only know fix is to format and reinstall.  When I first setup my system I installed Vista and then Ubuntu.  I don't want to reinstall my Ubuntu as it is working fine.  How can I reinstall my vista without touching my Ubuntu???

TIA

---

### Post by merlinus on 2009-07-12
You can use gparted to format your vista partition, and then the install cd will find it.  I do not believe vista is even capable of detecting linux partitions.

However, it will override grub, but it is very easy to reinstall afterwards.

Boot from the live cd, open a terminal and enter:

```
sudo grub
find /boot/grub/stage1  #you will get a response such as root (hd0,2)
root (hd0,2)    #use the numbers from the previous command
setup (hd0)
quit
```

---

### Post by Deadheded on 2009-07-12
Thanks much, seems easy enough.  Trying one last thing to save the Vista but I don't have much hope.  

Would luv to find the people who put out these trojans and the ones who spread them.  I would take 3 fingers from each hand.

---

### Post by theozzlives on 2009-07-12
> **Deadheded said:**
> Thanks much, seems easy enough.  Trying one last thing to save the Vista but I don't have much hope.  

Would luv to find the people who put out these trojans and the ones who spread them.  I would take 3 fingers from each hand.

Peoople would love to get ahold of murderers, rapist, and child molesters also. Some people are just sickos.

---

