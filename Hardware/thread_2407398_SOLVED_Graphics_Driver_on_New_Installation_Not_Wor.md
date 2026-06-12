---
title: "SOLVED: Graphics Driver on New Installation Not Working"
date: 2018-12-03
forum: Hardware
---

### Post by xtianmind on 2018-12-03
I installed Lubuntu onto an older HP Touchsmart Pc iq770.

Under update drivers, it says everything is up to date. But the color is off and you can tell it has bugs.

It had windows 7 previously and was working just fine. 

Under the display info it says,

Resolution: 1440x900
Vendor: The X.org foundation
Version: 1.19.6
Current display name:  :0.0

Does anyone know how to fix this?

[https://i.ibb.co/v3YcRvd/20181203-120500.jpg](https://i.ibb.co/v3YcRvd/20181203-120500.jpg)
[https://i.ibb.co/mbbRKLh/20181203-120609.jpg](https://i.ibb.co/mbbRKLh/20181203-120609.jpg)

---

### Post by deadflowr on 2018-12-03
Open a terminal and run
```
sudo apt install inxi
inxi -G
```
post back the output.
(inxi may or may not already be installed.
The first command will install it if not installed, you only need to post back the output from the second command.)

---

### Post by xtianmind on 2018-12-03
I fixed the problem. Thank you.

---

### Post by wildmanne39 on 2018-12-03
Please post your solution so the whole community can benefit.

Thanks!

---

