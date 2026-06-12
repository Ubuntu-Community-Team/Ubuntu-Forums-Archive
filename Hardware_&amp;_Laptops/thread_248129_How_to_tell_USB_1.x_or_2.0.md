---
title: "How to tell: USB 1.x or 2.0?"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by LotsOfPhil on 2006-08-31
I am wondering what a good way to check if your computer has USB 1.x ports or USB 2.0. My current best way to do this is:
```

[phil@USB2comp]$ cat /proc/bus/usb/devices | grep Spd
T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2

```
The Spd=480 means USB 2.0. On a USB 1.1 computer, I get Spd=12:
```

[phil@USB1comp]$ cat /proc/bus/usb/devices | grep Spd
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3

```
I don't understand why I get a mix in the first example and would like to know why. Or just a better (command line preferably) way to check.

---

### Post by LotsOfPhil on 2006-09-12
I'll just pass this through again.

---

