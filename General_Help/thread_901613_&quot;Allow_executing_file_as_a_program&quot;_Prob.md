---
title: "&quot;Allow executing file as a program&quot; Problem"
date: 2008-08-26
forum: General Help
---

### Post by JimboCorn on 2008-08-26
Well, i got a huuuge problem .....in the home folder properties, the permissions tab, there is a box where it says :"Allow execute file as a program" ....well i desactivate this an now i cant log in.....after doing that it drop me from the session and now i cant log in , every time that i try to log in it says that ive bben log in only for 10 sec and that is imposible to restore the session .......and as a advise says that i should try to log in in the filesafe mode .......i already try that but it shows the sam,e thing.....

   What i need is a way to change that "Allow execute file as a program" box throught the console.......if there is anyone who could help me....please.

---

### Post by Titan8990 on 2008-08-26
Typically, I would not recommend this buy try:

sudo chmod 744 -r /home/YOURUSERNAME

---

### Post by JimboCorn on 2008-08-26
it shows :"cannot access `744`:no such file or directory.....

---

### Post by JimboCorn on 2008-08-26
sorry ....it works......my bad.....it was with -R not -r......thanks

---

