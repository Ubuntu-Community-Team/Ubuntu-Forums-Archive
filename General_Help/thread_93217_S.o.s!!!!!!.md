---
title: "S.o.s!!!!!!"
date: 2005-11-21
forum: General Help
---

### Post by SkillZero on 2005-11-21
guys listen!!! i was an idiot,i have  installed all the nvidia updates i saw on syntapic,
i restarted my pc and when the boot loader comes up i have like 10-15 different linux boots.
i chose the default one and when the pc came up it had an error that said "your X is corrupted" something...and ask if i want to view details of it and stuff.
i dont know what to do. if someone can help me i will appriciate it.

---

### Post by Dr. Nick on 2005-11-21
10-15 that many??

When it boots up choose the recovery option then login, run ```
sudo nano /etc/X11/xorg.conf
``` and find the driver section, then change "nvidia" to "nv" and restart chosing the default option and it should get you back to X, you just wont have 3d acceleration until you get the drivers sorted out, which are easier once you get back into X

---

### Post by SkillZero on 2005-11-21
hm... i did that that but i could not find any nvidia line , except my graphic card line.. (Nvidia geforce blabla..)


-----------------
hey i tried again and found it. but i dont know how to save the changes? :|

---

### Post by Dr. Nick on 2005-11-21
if you were using nano hit ctrl+x then y i believe

---

