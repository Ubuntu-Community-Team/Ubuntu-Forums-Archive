---
title: "Hdd rpm"
date: 2011-07-14
forum: Hardware
---

### Post by sakishrist on 2011-07-14
Hello there,

Is there a way to see the current RPM of my HDD?

Thanks :)

---

### Post by haqking on 2011-07-14
> **sakishrist said:**
> Hello there,

Is there a way to see the current RPM of my HDD?

Thanks :)


you can

lshw

from terminal and then google the model to find out, should take about 10 seconds in total ;-)

or install smartmontools you could do a smartctl command from terminal

sudo smartctl -i /dev/sda

but you need smartmontools installed first

when it says model family it will show something like 7k200 which is 7200 rpm

---

### Post by sakishrist on 2011-07-14
Thanks [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

But that shows the "official" speed, not the current (live) one, doesn't it?

---

### Post by haqking on 2011-07-14
> **sakishrist said:**
> Thanks [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

But that shows the "official" speed, not the current (live) one, doesn't it?

you mean you want to know how fast it is currently operating at ?

in which case go to disk utility and do a benchmark

---

### Post by sakishrist on 2011-07-14
Well, my fault for not describing the question enough.

What I really need to see is the current rpm (not transfer speed) of the HDD. The reason I want to do that is because I have selected the option "Spin down hard disk when possible", so I would like to see how much the rpm is lowered. (just curious to see).

Thanks again and sorry for not being clear [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by haqking on 2011-07-14
> **sakishrist said:**
> Well, my fault for not describing the question enough.

What I really need to see is the current rpm (not transfer speed) of the HDD. The reason I want to do that is because I have selected the option "Spin down hard disk when possible", so I would like to see how much the rpm is lowered. (just curious to see).

Thanks again and sorry for not being clear [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Well when you go to see it will spin back up ;-)

spin down means put the HDD to sleep and use less power, as soon as you ask it to tell you what it is doing it will come alive again i would imagine.

the HDD spindown thing i dont think is much of an issue nowadays with more modern hard drives.

---

### Post by sakishrist on 2011-07-14
OK, Thanks a million!

---

