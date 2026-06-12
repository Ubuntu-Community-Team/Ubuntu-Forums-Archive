---
title: "How to make a windows program work.....?"
date: 2008-11-03
forum: General Help
---

### Post by azizmars on 2008-11-03
Okay well my dad owns a store and in his store he has cameras that he views on the computer online. I have a program called Remote Viewer that we use on windows. Now im wondering how do i make it work on ubuntu 8.10? If you need more info or something you can IM me on aim at AZIZMARS or send PM. Thx for the help guys.....

---

### Post by oldos2er on 2008-11-03
Have you tried Wine?

---

### Post by azizmars on 2008-11-03
No how do i download it or get it? Im srry im kind of new/noob at this.

---

### Post by Amerinidiot1231 on 2008-11-03
```
sudo apt-get install wine
```

run that in terminal

---

### Post by azizmars on 2008-11-03
> **Amerinidiot1231 said:**
> ```
sudo apt-get install wine
```

run that in terminal

Thx but now how do i let the program run throught wine?

---

### Post by Amerinidiot1231 on 2008-11-03
Chances are your program is compatible.

First if your install program is on cd, etc, you will need to insert that media and run the install program.  Double clicking it just like in windows should do the trick.  

It might delay for a second so be patient.  The install program will pop up and you can install just like in windows.

If you choose to make a start menu shortcut you can find that shortcut in  Applications-->Wine-->Programs

---

### Post by azizmars on 2008-11-04
Okay i did that and everything worked like you guys said. But when i go to the panel wine and programs i find the program there but it doesnt start when i press it. It says starting Remote viewer on the bottom panel that shows the programs but then it goes away. How do i fix that?

---

### Post by Amerinidiot1231 on 2008-11-04
That is most likely a compatibility issue with your program and wine.  I would suggest making a new post in the wine forum [HTML]http://ubuntuforums.org/forumdisplay.php?f=313[/HTML] and seek assistance there.

I looked up at appdb.winehq.org and found that your program has no compatibility notes. You can navigate to that site to seek assistance installing wine programs and you can see if a certain program is compatible.

If the program requires directx and you dont have direct 3d and accelerated graphics active that could very well be your problem as well.

---

