---
title: "How Disabling a Particular Fan"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by MrWendell on 2007-03-18
Hi Ubuntu forum members,

I am new to this forum but not an absolute beginner with Ubuntu. My question is regarding a particular fan on my system. 

I have installed lm-sensors on my system with success no problems. Played around with the settings as well to get the min- and maxtemp rates associated with the PWN values. 

The question I have, is there a way to disable a particular fan or alter the RPM without having temperature relation (MINTEMP/MAXTEMP) to it ? This is because one of my fans does not have temperature sensor attached to it (the system just not seems to recognize it) 

I would appreciate if one can give me some support. Thx

---

### Post by Erlander on 2007-03-18
If you are sure it is not needed all you have to do is to disconnect it either from the motherboard or the power supply depending on how it is connected.

Rob

---

### Post by MrWendell on 2007-03-19
True... But I was hoping that maybe I can not only disable it but to slower its speed down. The fan is working with 6,240 rpm, you could imagen how much noise it is producing. 

I know of any option with /proc/acpi/.../fan0  fan, with echo "0" > fan/state option but I do not have two fans displayed there. But two fans displayed with lm-sensors...that is why I wound like to know how I could disable the one in lm-sensor, or just to slower it down.

---

### Post by Erlander on 2007-03-19
Another option is to supply it with either 5 or 7 volts by connecting it differently to the power supply.

Rob

---

### Post by MrWendell on 2007-03-19
Agree... Is there any other solution then hardware?

I know Erlander I can also switch off the PC to get rid of the fan spinning... lol

I need though a software solution. And I am sure it is possible, as the fan exists and it is just a setup thing.

---

### Post by Erlander on 2007-03-19
Suggestion:  Do an advanced edit of your original post and change the title to something like:  "Software Control of Fan Speed".

You may get other responses that are more to your needs.

best wishes.

Rob

---

### Post by MrWendell on 2007-03-19
I could... and I guess I will

---

