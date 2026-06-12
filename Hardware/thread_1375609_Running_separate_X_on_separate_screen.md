---
title: "Running separate X on separate screen"
date: 2010-01-08
forum: Hardware
---

### Post by denix on 2010-01-08
Hi all, sorry for the noob question but I'm really unable to sort it out!
I have an experimental monitor for which I wrote a special X configuration file and I have also a normal samsung monitor both of them connected to an NVidia GeForce 9800 GTX+.
What I would like to do is to run X with the special setting on the experimental monitor and a normal session on my normal monitor to work on the workstation.
Is it possible? if yes, how?

many thanks,
Denis

---

### Post by llamaSniper on 2010-01-08
have you tried ctrl+alt+F1, login, and use startx? I think that should start a different xserver, but I don't know if you can use that on 2 monitors at once. ctrl+alt+F7 to go back to the regular xserver if it doesn't work.

---

### Post by llawwehttam on 2010-01-08
I don't think you can have more than one xserver running at once.
sorry.

---

### Post by llamaSniper on 2010-01-08
but couldn't you use 2 different terminals at the same time? I'm not sure as I only have one monitor, but it may work...

---

### Post by llawwehttam on 2010-01-08
Yes you can have two different terminals working but they will not show on different screens. The best you can do is to use the graphics drivers to set up a dual display. Without serious work you cannot have two instances of the xserver running on the same machine.

---

