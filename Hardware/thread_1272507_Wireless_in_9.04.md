---
title: "Wireless in 9.04"
date: 2009-09-22
forum: Hardware
---

### Post by bwisdom on 2009-09-22
Hello,

Ive recently installed ubuntu 9.04 along side my XP install on my laptop and everything is working great. The only slight problem I have is with the wireless networking.

Everything is working just fine its just that when I move to a new wireless spot I have to start my laptop up on windows first in order for the card to work in ubuntu. Here is my example:

I use my laptop at home (wireless router) and I use my laptop on campus (wireless access points). Now when I first get home I have to start my computer up on windows in order for my wireless card to even work on ubuntu to see the network. After that I can shut the computer down, switch distros, do anything and will still be able to go back to ubuntu and get on the wireless without having to start windows. Then when I go to campus its the same thing, the card doesn't work until I boot up windows on campus and then switch back to ubuntu.

Is there something wrong with the drivers? Or am I just missing something really simple.

---

### Post by Bucky Ball on 2009-09-22
Next time you are in the situation where you are going to need to boot Windows to get networking going, boot into Ubuntu instead, open a terminal (Applications->Accessories->Terminal) and copy/paste in this command:

```
sudo /etc/init.d/networking start
```Did that start the network? What happened? It sounds like you have something missing in your startup files.

---

### Post by whitehaint on 2009-09-22
Rather interesting, I use a laptop on wireless at home and school and have had no issues.  Drivers up to date?

---

### Post by scrooge_74 on 2009-09-22
OP dosent tell which brand of wifi card he has since different cards have different drivers or problems with different versions of Ubuntu

---

### Post by bwisdom on 2009-09-22
Ill try that when I go home tonight cause thatll be the next time the card wont be working for me.

As far as what wireless card, I have the Intel PRO/Wireless 3945ABG Network Connection card.

---

### Post by kirob on 2009-09-22
I'm having the same problem with a home network using the Netgear DG834G router. I've got a dual boot setup on a Dell Inspiron 1300 with a Celeron M processor. The Wifi card is the Dell 1370 802 mini PCI card.
 
The Windows XP partition works perfectlly. Ubuntu 9.04 is installled on a separate partition and there is no wireless connection.  Can  anyone suggest a solution

---

### Post by Bucky Ball on 2009-09-22
> **kirob said:**
> I'm having the same problem with a home network using the Netgear DG834G router. I've got a dual boot setup on a Dell Inspiron 1300 with a Celeron M processor. The Wifi card is the Dell 1370 802 mini PCI card.
 
The Windows XP partition works perfectlly. Ubuntu 9.04 is installled on a separate partition and there is no wireless connection.  Can  anyone suggest a solution

Plug in an ethernet cable and get your updates if you haven't already.

---

