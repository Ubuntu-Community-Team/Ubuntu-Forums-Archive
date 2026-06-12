---
title: "Disable GDM"
date: 2008-09-30
forum: General Help
---

### Post by anotherdisciple on 2008-09-30
I'm a geek, so I like turning off some of the graphical stuff so I can see a black screen with white text... I'm not sure why I like it.

I turned off my usplash... so now I get to see all the text scrolling through when ubuntu is loading, but what happens if I turn off the gdm service?

I was planning on going to (System > Administration > Services) and turning it off. will this just give me a command prompt that asks for my name and password? That's what I want.

---

### Post by Nepherte on 2008-09-30
You could tell Ubuntu to start in run level 3 instead of level 5. Another option is to remove gdm from the rc.x directories. You will get a console with both methods. You can start your desktop environment with the startx command or start up gdm again. Disabling GDM from system > administration > system services should do the trick.

---

### Post by zvacet on 2008-09-30
```
sudo /etc/init.d/gdm stop
```

---

