---
title: "Hdd temp monitor"
date: 2013-04-24
forum: Hardware
---

### Post by ketchup94 on 2013-04-24
I am having a hard time locating and displaying my temperature. I have tried an hdd temp command hoping to find it but I have had no luck yet. Any suggestions, I am not the best at Linux.

---

### Post by tgalati4 on 2013-04-25
Open a terminal, what is the output of:

```
sudo hddtemp -D /dev/sda
```

It should look something like:

tgalati4@Mint14-Extensa ~ $ sudo hddtemp -D /dev/sda
[sudo] password for tgalati4: 

================= hddtemp 0.3-beta15 ==================
Model: WDC WD1600BEVS-22RST0

field(1)	 = 1
field(3)	 = 155
field(4)	 = 217
field(5)	 = 0
field(7)	 = 0
field(9)	 = 80
field(10)	 = 0
field(11)	 = 0
field(12)	 = 237
field(192)	 = 32
field(193)	 = 11
field(194)	 = 40
field(196)	 = 0
field(197)	 = 0
field(198)	 = 0
field(199)	 = 0
field(200)	 = 0

If one of the field value seems to match the temperature, be sure to read
the hddtemp man page before sending a report (section REPORT). Thanks.

In this case my disk temperature is 40C and that is what shows in my instrument panel.

It went up 1C:

tgalati4@Mint14-Extensa ~ $ sudo smartctl -a /dev/sda | grep 194
194 Temperature_Celsius     0x0022   106   086   000    Old_age   Always       -       41

---

### Post by gordintoronto on 2013-04-25
Or just:
sudo hddtemp /dev/sda

---

### Post by Feathers McGraw on 2013-04-25
Have you tried psensor? It'll give you a GUI where you can monitor the temperature of all the sensors a available to it (e.g. Hard drive, cpu, graphics card). It can also draw graphs of temp against time. 

Feathers

---

