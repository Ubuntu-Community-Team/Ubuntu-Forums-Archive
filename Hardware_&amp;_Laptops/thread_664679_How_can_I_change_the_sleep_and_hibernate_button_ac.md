---
title: "How can I change the sleep and hibernate button actions in gnome"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-01-11
Specifically, I have a Dell Vostro 1400. The fn-F2 combination is the little crescent moon shape, which, to me, means "suspend", not hibernate. But for some blasted reason Gnome keeps hibernating my system. How can I reassign this?

Thanks.

---

### Post by Yellow Pasque on 2008-01-11
Check the setting in System -> Preferences -> Power Management. Look under the "general" tab.

---

### Post by enigma_0Z on 2008-01-11
Tried that already--modified the "When the suspend button is pressed:" option--changing it to suspend, or hibernate, or do nothing, and it doesn't work with any option...

---

### Post by Yellow Pasque on 2008-01-11
Ok. Type the following in a terminal:
```
sudo gconf-editor
```
Once the Configuration app comes up, pull down the apps tree (i.e. click the arrow next to the word 'apps'). Then do the same with 'gnome-power-manager'. I'm guessing the setting you'll want to change is in the 'buttons' folder, because Gnome seems to think your suspend button is a hibernate button. Right-click on the hibernate key and change its value to suspend. I've attached a screenshot with the key you need to change highlighted in case that confuses you.

---

### Post by enigma_0Z on 2008-01-12
That worked, thanks!

---

