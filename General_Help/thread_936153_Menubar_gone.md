---
title: "Menubar gone"
date: 2008-10-02
forum: General Help
---

### Post by usstitan on 2008-10-02
Hi all, installed Ubuntu 8.04 a few days ago and everything has been going fine so far. Booted up today though to find the menu bar is gone as well as the one on the bottom with the recycle bin. All there is on my screen is my desktop background and I can't access anything. Luckily was able to launch firefox with a shortcut on my keyboard but that is all i can do. Any help would be much appreciated.

---

### Post by Ryadt on 2008-10-02
Do Alt+f2. Then```
gnome-terminal
```
Type this in terminal```
sudo apt-get install gnome-panel
```

---

### Post by usstitan on 2008-10-02
thanks for speedy reply, unfortunately nothing is happening when i press alt+f2. Any other suggestions?

---

### Post by Ryadt on 2008-10-02
Try Ctrl+Alt+F1.Then run the code. Ctrl+Alt+F7 to get out of terminal mode.

---

### Post by usstitan on 2008-10-02
Thanks very much, that has solved the problem. menu bar is back now.

---

### Post by Tiddens on 2009-12-11
It didn't work for me!  I upgraded from Ubuntu 9.04 to 9.1 and lost the menu.  This is nuts!  You can't have people upgrade their systems and become paralyzed by losing any menu to click on!  I'm really trying to be a Windows to Ubuntu convert, but this is crazy!

---

### Post by Indigothecat on 2011-02-26
Hi 

I have also lost the bottom menubar with rubbish bin etc. I now lose any minimised programs as I can not see them as a minimised tab etc. I can find them using the rotate cube option (Alt + Tab). Trying to fix this is a pain for a complete newbie any advice would be a great help. 


thanks
I

---

### Post by Script Warlock on 2011-02-26
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel

---

