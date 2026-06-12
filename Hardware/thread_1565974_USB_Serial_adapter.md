---
title: "USB Serial adapter"
date: 2010-09-01
forum: Hardware
---

### Post by obroden on 2010-09-01
Hi,

I have a little troubble using my GPS together with my computer.

I have a SAmsung N220 and Im running Netbook edition. I also have a Silvamultinavigator GPS.

 The problem is that the GPS connects via a USB serial adapter to ttyUSB0. In Fugawi the map program I can only choose from ttyS0-3.

My question is: Is there any way to "clone" the ttyS0 with the ttyUSB0, my computer does'nt have any real serialports.

the gpsd is using port: 2947

Thanks,

/Oskar

---

### Post by IcarusR on 2010-09-02
Yes you can create a soft link using the 'ln' command see the man page

```
man ln
```

---

### Post by obroden on 2010-09-03
Hmm.. maybe I did it wrong.. I typed in ln /dev/ttyS0 /dev/ttyUSB0

it responded: creating hard link "/dev/ttyUSB0" file exists

now, when I run Serial port terminal and try to see the communication going on to USB0 it says: can not open /dev/ttyUSB0 : Unit or resource is busy.

Then I thought Id figured out how to fix the problem, this was not the case. ANyways I wrote: rm /dev/ttyS0 and then ln -s /dev/ttyUSB0 /dev/ttyS0. This resulted in that now the Serial port terminal allso says the same thing about ttyS0 when I try to check it as it did for the USB0..

can anyone please help me out here?

Thanks!

Oskar

---

### Post by obroden on 2010-09-05
Can anyone please see what I did wrong? 

I don't quite understand how this works...

/Oskar

---

