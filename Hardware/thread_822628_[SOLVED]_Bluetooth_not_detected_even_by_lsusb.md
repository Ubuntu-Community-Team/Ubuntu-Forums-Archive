---
title: "[SOLVED] Bluetooth not detected even by lsusb"
date: 2008-06-08
forum: Hardware
---

### Post by ztrange on 2008-06-08
Hello, 

I have a Toshiba Satellite U305 5107 with bluetooth capabilities. I installed Hardy from a burned iso. This is not my first ubuntu install neither my first linux. Before Hardy I used to have Gustsy on the same laptop and I could see my bluetooth device in lsusb.

I'm aware that maybe Ubuntu will not be able to use my bluetooth but I really want it to be listed in lsusb so I can use it with Virtualbox as USB hardware. 

Well, i really don't know where to begin, Ive searched the forums and Google but so far, no luck.

I hope that someone here can give me some advice.

Sorry for my english.

Regards

---

### Post by ztrange on 2008-06-08
Well, now its fixed, Ubuntu doesnt detect it in hcitool dev but I can see it in lsusb. 

What I did was:

sudo /etc/init.d/bluetooth stop/start/restart

in this case I used start.

---

