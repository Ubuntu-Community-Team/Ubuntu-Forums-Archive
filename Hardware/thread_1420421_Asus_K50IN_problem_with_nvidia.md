---
title: "Asus K50IN problem with nvidia"
date: 2010-03-03
forum: Hardware
---

### Post by CrowBelgrade on 2010-03-03
I have Asus K50In with Nvidia 102 m graphic card,and I try to instal 10.04 alfa 3. First problem is I can not see GUI when I start Live CD. I solved that problem with F6 nomodeset. When I install Ubuntu and try start OS I got this
[http://img9.imageshack.us/img9/8486/02032010.jpg](http://img9.imageshack.us/img9/8486/02032010.jpg)

---

### Post by Jared Norris on 2010-08-14
Were you able to get this working at all? There is another member in our loco that is having the same problems and I'm running out of ideas to try.

Thanks in advance.

---

### Post by ghettobird on 2010-08-14
Most of everything I've butchered has been ASUS products. What kind of BIOS is it and how is it configured? It's hanging on the BIOS start screen and staying there. I had a similar problem and became highly irritated and flashed the CMOS and got rid of the startup screen and then edited the GRUB menu "E" when it hits and deleted the line which has the quiet splash and entered nomodeset. I'm not 100% positive this is the direction for you to go as flashing a BIOS is extremely risky, but I'm sure someone will chime in eventually.

---

