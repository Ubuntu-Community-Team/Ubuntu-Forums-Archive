---
title: "Battery life ubuntu 10.04"
date: 2010-06-28
forum: Hardware
---

### Post by wilstar on 2010-06-28
Hi all,
when i've installed ubuntu 10.04 on  my laptop (Vostro 1510), i've had problems with the battery (short battery life).

What is the solution? May be to install laptop-mode-tools with the command
```
sudo apt-get install --no-install-recommends laptop-mode-tools sdparm ethtool
```

thanks.

---

### Post by quirkification on 2010-06-28
Well, it does make a slight difference to my battery life when I use the *CPU Frequency Scaling Monitor* on the panel. You can set your cpu, or both if it is dual core, to powersaving mode.

I fiddle with it a lot, you can change CPU setting to run at a constant low 1.2ghz or... here's my list.

2.1ghz
1.6ghz
1.2ghz
on demand
conservative
performance
powersaver

And mind you, this is independent for each cpu, if that helps you at all. I know i have added about 40min or 1 hour by using powersaver. (according to the power consumption charts)

---

