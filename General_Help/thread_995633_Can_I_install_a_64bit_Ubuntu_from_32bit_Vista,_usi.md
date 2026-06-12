---
title: "Can I install a 64bit Ubuntu from 32bit Vista, using WUBI?"
date: 2008-11-28
forum: General Help
---

### Post by aneslin85 on 2008-11-28
Hai all
I bought a new HP Pavilion DV5 1126em Laptop.
and it comes with pre installed Vista Home Premium 32bit with 3GB Ram.
CPU - Core2Duo 2.0 Centrino 2 (P Series), 
Ram - 3GB DDR2 ( Max Ram capacity is 8GB )

but it will support 64bit OS, and I have all 64bit Windows Drivers. 
( BUT There are no drivers for Linux in HP site :( )

Now here is my scenario, 
Currently am using 32bit Vista, but i would like to use 64bit ubuntu 8.10
and I would like to install it using Wubi.
Can I install a 64bit Ubuntu from 32bit Vista?
and Where can I get the Linux Drivers?

( I dont have any idea to install it without Wubi, )

and it will Run with my 3GB DDR2 ? or Do i need to put 4GB?

Thanks in advance guys :)

---

### Post by aneslin85 on 2008-11-30
guyzz pls help me

---

### Post by Skripka on 2008-11-30
> **aneslin85 said:**
> Hai all
I bought a new HP Pavilion DV5 1126em Laptop.
and it comes with pre installed Vista Home Premium 32bit with 3GB Ram.
CPU - Core2Duo 2.0 Centrino 2 (P Series), 
Ram - 3GB DDR2 ( Max Ram capacity is 8GB )

but it will support 64bit OS, and I have all 64bit Windows Drivers. 
( BUT There are no drivers for Linux in HP site :( )

Now here is my scenario, 
Currently am using 32bit Vista, but i would like to use 64bit ubuntu 8.10
and I would like to install it using Wubi.
Can I install a 64bit Ubuntu from 32bit Vista?
and Where can I get the Linux Drivers?

( I dont have any idea to install it without Wubi, )

and it will Run with my 3GB DDR2 ? or Do i need to put 4GB?

Thanks in advance guys :)


There really isn't that much of a reason to run 64-bit with only 3GB RAM, sure you can-but there really is no advantage.


I have no answer for you regarding WUBI, but my HP Photosmart 6200 series installed easy under 64bit.  There usually is no need to worry about hunting for drivers in linux, graphics drivers can be gotten from Synaptic, Ubuntu comes with ALSA sound drivers, and printers install via whatever printer management utility you use.

---

### Post by ago on 2008-12-01
Yes you can, in fact that will be the default

---

### Post by aneslin85 on 2008-12-03
Thanx Skripka and Thanx ago.

---

### Post by Jammanuser on 2008-12-03
> **ago said:**
> Yes you can, in fact that will be the default

Are u saying then that the default ISO that wubi installs is the 64-bit version??? :shock::shock::shock::shock: i was under the impression that it was 32-bit...so does that mean if it is 64-bit, that i wont be able to install ubuntu 8.10 on a **separate partition**, because i have a 32-bit system??? ;)

Looking forward to ur reply...

-jammanuser

:D

---

### Post by ago on 2008-12-06
Wubi detects the processor architecture and if it supports 64 bits it downloads and installs Ubuntu 64, otherwise you get Ubuntu 32. That can be overridden with special commandline arguments or by providing the ISO.

---

### Post by Jammanuser on 2008-12-06
> **ago said:**
> Wubi detects the processor architecture and if it supports 64 bits it downloads and installs Ubuntu 64, otherwise you get Ubuntu 32. That can be overridden with special commandline arguments or by providing the ISO.

ahh...ok...i get it now! :) so the version that I probably have then is the 32-version...because i have a 32-bit Vista? Or does the current OS not have an effect on which version Wubi chooses? ;)

Looking forward to ur reply... :)

-jammanuser

:D

---

### Post by ke9v on 2008-12-06
> **Jammanuser said:**
> ahh...ok...i get it now! :) so the version that I probably have then is the 32-version...because i have a 32-bit Vista? Or does the current OS not have an effect on which version Wubi chooses? ;)

It doesn't matter what version (32 or 64 bit) of Vista you are running. If your PC is capable of running the 64-bit version of Ubuntu it will be installed by default with Wubi. As previously noted, if you have a 64-bit capable processor but want the 32-bit version of Ubuntu, there is a command line switch to use it instead of the default. Check the FAQ section of the Wubi site for more details.

Good luck.

Jeff

---

### Post by Jammanuser on 2008-12-06
> **ke9v said:**
> It doesn't matter what version (32 or 64 bit) of Vista you are running. If your PC is capable of running the 64-bit version of Ubuntu it will be installed by default with Wubi. As previously noted, if you have a 64-bit capable processor but want the 32-bit version of Ubuntu, there is a command line switch to use it instead of the default. Check the FAQ section of the Wubi site for more details.

Good luck.

Jeff

ok...cool! Thanks! actually, i really want the 64-bit version, if u don't mind...and since that it is the default, then i shouldn't have to use the command line for that! ;)

Cheers! :)

-jammanuser

:D

---

### Post by aneslin85 on 2009-01-22
thanks a lot guys.

---

