---
title: "LCD off: during boot/after waking up from inactivity/after suspension"
date: 2018-12-09
forum: Hardware
---

### Post by geladynata on 2018-12-09
This is my first time asking something here, so please be as tolerant as possible with any mistake that I make.
  
The problem:

  
[LIST]
[*]I have installed ubuntu 18.10 and (sometimes ~70% chance) when I  boot up the laptop I see a purple screen and then the lcd turns off  (just black, without light). 
[*]The same happens 99% of the times, if i leave the laptop for some  minutes in inactivity. When I come back, I press buttons or move the  mouse and the lcd remains dead. 
[*]The same happens 99% of the times, if I wake the laptop from suspension. 
[/LIST]
  
While the screen is turned off, I can hear sounds if I hit the volume  up/down buttons. Furthermore, I can blindly log in, then press  Ctrl+Alt+T, write reboot and press enter (all these blindly), and the  laptop reboots, prossibly to the same situation.


  I tried the "nomodeset" trick and it worked, but I get a wrong  resolution and extremely bad graphics performance, rendering the laptop  unusable. The same goes for "radeon.modeset=0".

The same thing happend with Lubuntu 18.04.

Is there any possible solution to this problem? Thanks in advance for any suggestions.
  
Laptop model: HP pavilion dv6 1120ev 
Graphics: ATI Mobility Radeon HD 4530


```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v] [1002:9553]
    Subsystem: Hewlett-Packard Company Mobility Radeon HD 4530 [103c:3628]
    Kernel driver in use: radeon
    Kernel modules: radeon

```

---

