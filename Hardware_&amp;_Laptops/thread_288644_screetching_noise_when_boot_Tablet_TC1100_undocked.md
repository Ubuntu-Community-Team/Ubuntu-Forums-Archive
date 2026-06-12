---
title: "screetching noise when boot Tablet TC1100 undocked"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by chindogucci on 2006-10-30
I've been running Dapper and Edgy successfully on my HP TC1100 tablet PC, but have found one problem under both Dapper and Edgy - if I boot up when the computer is undocked, the machine makes a truly unbearable earsplitting shrieking noise from the built-in speakers (not from internal beep).

The terrible noise also happens if I hot-undock without restarting the machine.

If I boot up in the docking station, its all fine and there is no noise. Anyone got idea what is going on?

THanks

---

### Post by lingnoi on 2006-11-29
Try typing

```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the following line to the bottom of the file:

```
options snd-hda-intel position_fix=1 model=3stack
```

---

