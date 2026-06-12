---
title: "Randomly stops working"
date: 2008-08-15
forum: General Help
---

### Post by Hyper Tails on 2008-08-15
Hi i got vista and hardy installed on a pc built 2 months aga and for some reason

i'm on hardy and for some reason the screen goes black and show 

hardware check  ok and other checks and stays there until i restart the machine

help will be thanked

---

### Post by MonctonJohn on 2008-08-15
Sounds like the Xserver died. Did you try to see if X is still up (press ctrl + alt + f7). If its dead you can still log into a console by pressing ctrl + alt + f2. From there you can try to figure out what happended: ps -e | grep gdm.

This will tell you if gnome is still running. Try those suggestions as a start and let us know if X died or not.

---

### Post by Hyper Tails on 2008-08-17
I think you may know what i'm talking about but just incase heres a photo of it

---

### Post by Hyper Tails on 2008-08-19
?

---

