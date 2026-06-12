---
title: "I can't install any distribution"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Visentem on 2009-06-22
Hi,

I'm trying to install ubuntu in a desktop computer with AMD Sempron, 512 RAM. 

When I install Ubuntu from the live CD, after the uspash charges, the screen turns black. 

That happens with all the distributions I've tried : ubuntu (9.04), kubuntu (9.04), openSUSE (11.1), Fedora (11)...


Anyone knows what's the problem?
Thanks

---

### Post by masux594 on 2009-06-22
I think it isn't a OS problem.. Maybe your pc that is goning crazy =P? Seriously, when happend?

Sysc, A

---

### Post by madverb on 2009-06-22
What is the motherboard you are using?

---

### Post by wpshooter on 2009-06-22
Have you tried installing with the safe graphics mode parameter.

If that does not work, the try installing from the ALTERNATE (text based) CD version of Ubuntu instead of the live CD version.

---

### Post by Visentem on 2009-06-22
Actually I don't have any OS and I don't know how to see my hardware settings.

That happened yesterday. The computer is old. It was forgotten in a room.

I know it had problems with a wireless networking hardware. I think the computer didn't detect it, but that was with XP.

I'll try with the ALTERNATE...

---

### Post by Findarato on 2009-06-22
Hello there.

I think I once had exactly the same problem as you do here. A friend kindly came over and fixed it by manually changing the driver used. In my case, there was a problem with the nvidia legacy driver...

You could try dpkg-reconfigure xserver-xorg maybe ?

---

### Post by Visentem on 2009-06-22
> **Findarato said:**
> You could try dpkg-reconfigure xserver-xorg maybe ?

Where do I have to put it?

---

### Post by masux594 on 2009-06-22
the answer is "in a terminal".. But, if u can't install the os.. ..you can't type this line in a terminal.. If i understand, you can't do nothing from the first loading.. ..i suppose that the problem isn't the CD or the OS .. Maybe a HW problem..

Sysc, A

---

### Post by Findarato on 2009-06-22
> **Visentem said:**
> Where do I have to put it?

If I got it right, the distribution starts from the CD, installs and ONLY THEN you get the black screen, right ?

If so, you can switch into text-mode by alt+f7 (or f6?). You can then use the dpkg-reconfigure xserver-xorg or manually find the xorg.conf (if it is even called like that)

---

