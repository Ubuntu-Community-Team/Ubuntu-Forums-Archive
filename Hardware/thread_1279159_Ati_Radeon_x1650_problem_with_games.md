---
title: "Ati Radeon x1650 problem with games"
date: 2009-09-30
forum: Hardware
---

### Post by corl45 on 2009-09-30
Alright from what I understand the proprietary drivers from ati don't work on 9.04, so ubuntu has to use open source drivers which don't support all features of certain video cards yet? so is there any way to get the games running? i have compiz desktop effect running seamlessly, so is there any way to get the FPS games working? like a workaround? games such as saurbraten?  or will I just have to wait untill the opensource drivers are updated?


acer ase571
intel core 2 duo 1.8 ghz
3 gig ram
320 gig hard drive

---

### Post by Yellow Pasque on 2009-09-30
sauerbraten requires OpenGL 2.x features, which the ATI mesa DRI drivers don't support at the moment.

If you were happy with fglrx, you can always downgrade your xserver so that you can install fglrx/Catalyst 9-3 (a lot of people have done this). Search for it.

---

### Post by corl45 on 2009-09-30
Alright thanks! Ill look it up.

---

