---
title: "Sony VAIO VGN-S5HRP / VGN-S580 hangs during installation"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by serhio on 2006-06-30
Yello everybody

my sony VAIO VGN-S5 which is VGN-S580 name outside USA completely hangs during installation.

it always happens when formatting partitions (I do it manually to prevent windows destruction)

as it said here: 
[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVGN-S580P?highlight=%28sony%29]("https://wiki.ubuntu.com/LaptopTestingTeam/SonyVGN-S580P?highlight=%28sony%29")

this problem must have fixed in Breezy, why does it again happens in DapperDrake?

thanx for any help

---

### Post by jarviw on 2006-06-30
try adding "**acpi=off**" at the *end* of your booting command.

I had that problem while installing Dapper in my VAIO PCG-FX120 (old!) NB, too.  
but for whatever odd reason, adding acpi=off at the end of the booting command worked.

---

### Post by martinoc on 2006-06-30
I'm experiencing the same problem with my sony VGM-A517M
If I use the alternate install cd, I can install but then when it boots
the kernel panics.

---

### Post by martinoc on 2006-06-30
I've tried adding the acpi=off to the live cd boot but this does not work for me.
If I use irqpoll it will boot but the disks will get confused when I try to install, although it will manage to create partitions.

---

### Post by serhio on 2006-07-01
thanx for your answers guys... but it still doesn't work.
it hangs while coping files now.

and it seems like it's overheated...

---

### Post by Hellkeepa on 2006-07-01
HELLo!

Well, since none of the other suggestions worked, and you say it seems to be overheating.
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

That might help, as I haven't had any real issues with heat or performance since I went to the -386 kernel.

Happy codin'!

---

