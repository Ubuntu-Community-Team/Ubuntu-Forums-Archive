---
title: "Dell Vostro A860"
date: 2009-08-05
forum: Hardware
---

### Post by Gyilkos on 2009-08-05
Hi,

*Intro*
This is my first laptop and i didnt watch the battery life when updated the system, and it turned off in the middle of it( i know its a very stupid mistake ). My factory ubuntu died, so i reinstalled it from the Ubuntu 8.04 lts dvd ( shipped with the laptop ) but its not the same.

-Where can i get the same ubuntu 8.04 iso?
-What is the apt reposirtory of dell for this laptop? ( not the dell-mini i think. i cant find it on the net )

If someone got the same laptop with the factory ubuntu plz check it (/etc/apt/sources.list)

Sry for my english.

Regards.
Adam

---

### Post by Gyilkos on 2009-08-05
Maybe its on the 5gb partiton(sda2) :), i'll try it tomorrow.

---

### Post by Gyilkos on 2009-08-06
Success. I reinstalled it from the Dell partition, now i have the factory ubuntu.

I had to add these lines to the boot/grub/menu.lst

```

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

```

First i tried the manual reinstall but it stopped at boot after install, the automatic reinstall worked fine.

If anyone intrested in the repsoitory, here it is(but its useless without the factory os i think):
```

deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

```
Peace.

---

