---
title: "hacking wifi card and good wifi pcie card?"
date: 2015-03-15
forum: Hardware
---

### Post by Johannes33 on 2015-03-15
I was looking for a good wifi card for my laptop. 
It is a toshiba satellite p750-10R. but I dont think that matters so much. 

What is important is what half size PCI-E card with good reception and no problems with drivers exist out there. 
Since 5300 and 6300 has general good reception in windows perhaps they are good choices even for linux?

All input will be appreciated. 

An extra question if someone knows:

 I have an Ultimate-N Intel 6300 633ANHMW FRU 60Y3233 wificard. 
But it wont work on my toshiba since it is lenovo branded. :(

But according to some posts on the internet (look [here]("http://fx.cz/sklad/intel/")) it is supposed to be able to change the setting of a wifi card so it will be a normal intel 6300 and not lenovo. 

The posts I have found are for older cards and not for 6300 so I dont know if it is still possible. Does anyone know? :KS

---

### Post by Bucky Ball on 2015-03-15
Welcome. With the ultimate-n card installed, reboot and please give the result of this from a terminal:

```
sudo lshw -C network
```

Which release of Ubuntu are you using? Also, get online with a cable, update the machine and reboot. Anything?

---

