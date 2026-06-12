---
title: "Tryed getting my 9600 gt to work... but"
date: 2008-08-26
forum: Hardware
---

### Post by G-Dub on 2008-08-26
I tried getting my 9600 gt to work  by following these directions:

> **hotweiss said:**
> You are in luck, Envy has the new Nvidia drivers as of June 11th.

1. sudo apt-get remove nvidia*
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.


Unfortunately, it did not work for me. On top of that, somehow it delete or disabled my wireless card drivers and i no longer have an internet connect!!!!! It is extremely frustrating. Any ideas?

---

### Post by G-Dub on 2008-08-26
I did some further investigating. It appears as though Kubuntu recognizes both devices. But they are disabled. And the drivers don't appear in the list of drivers. Please, anyone have thoughts? I'm really stuck here.

---

