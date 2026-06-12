---
title: "compiz auto start??"
date: 2008-08-08
forum: General Help
---

### Post by Kaneda187 on 2008-08-08
how do i make copiz load window manager without going to the compiz-fusion icon then hitting reload window manager every time i start up?

cheers!!

---

### Post by UbuntuNerd on 2008-08-08
try adding it to your start-up programs in System>>Preferences>>Sessions. Add a startup program, call it whatever you want, and have the command be 'compiz --replace'.

also you can try 'compiz --replace &' in a terminal and see if that helps

---

### Post by sayakb on 2008-08-09
You can also System->Preferences->Appearance->Visual Effects and click **Extra**.

---

### Post by armandoxxx on 2008-11-16
This is what helped me ! ... 

I installed compiz-fusion icon and set to use compiz as window decorator .. then I also set System->Preferences->Appearance->Visual Effects -> Extra.

when I loged in both tried to load compiz .. so I disabled System->Preferences->Appearance->Visual Effects -> Extra. and let compiz fusion icon to load it .. now it works fine ! 

bye 
Armando

---

