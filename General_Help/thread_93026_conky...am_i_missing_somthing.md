---
title: "conky...am i missing somthing?"
date: 2005-11-21
forum: General Help
---

### Post by sunrex on 2005-11-21
> darksoul@network:~$ conky
Conky: can't open '/sys/bus/i2c/devices/0-0050/1_input': No such file or directory
please fix i2c or remove it from Conky
darksoul@network:~$







any ideas?

---

### Post by Pablo_Escobar on 2005-11-21
Hmmmm, maybe something in Your conky config is reffering to the '/sys/bus/i2c/devices/0-0050/1_input'.
You should browse through the conky setup and find what You need and what You don't need.

---

### Post by mcduck on 2005-11-21
Error with i2c points to motherboards temperature/voltage sensors. Have you configured lm-sensors? You should do some changes to those lines in conkyrc, to fit your motherboards sensors setup.

I can't help much with that, as it depends on your motherboard and it's sensor chip, but if you just want to get conky workin quickly you could also remove all those lines from your conkyrc.

---

