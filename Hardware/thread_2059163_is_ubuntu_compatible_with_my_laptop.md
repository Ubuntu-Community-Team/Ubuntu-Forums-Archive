---
title: "is ubuntu compatible with my laptop"
date: 2012-09-17
forum: Hardware
---

### Post by TheVamPiRe on 2012-09-17
Hello guys i use windows 7 but i m a great lover of ubuntu i would love to install it but i must first know if its compatible with it here is my computer performance
[I][B][CENTER]Type: Hp Compaq Presario CQ56
RAM: 3GB
Procesor: Pentium(R) Dual-Core CPU T4500 @ 2.30GHz 2.30 GHz
System Type: 64-bit Operating System
Graphic Card: Mobile PC Display
Wifi: Yes[/CENTER][/B][/I]
Can someone tell me if my computer is compatible with Ubuntu? :)

---

### Post by ajgreeny on 2012-09-17
It probably will run it OK, but it is almost impossible to say from the specs you have given.  Computer manufacturers are very likely to change the detailed specification of their machines, with different cpu, graphic card, and wireless chips being used over the life of the various models, so the best answer is for you to get a live CD/USB of the latest version of ubuntu and see if it runs and finds the wireless connection that you want to use.

If the live system runs OK, the installed system should also do the same.

If there are problems you can get more info on the detailed specification by booting  the live CD and running the command ```
sudo lshw -c network -c display
```in terminal which will show exactly what the graphic card and wireless card in the machine are.

---

