---
title: "No Dvorak Keyboard Layout?"
date: 2005-12-02
forum: General Help
---

### Post by Kenji Miyamoto on 2005-12-02
I've checked around a bit, and haven't found the Dvorak keyboard layout as an option.  Would editing xorg.conf manually be the only method of doing this?

---

### Post by Qrk on 2005-12-02
Its there...

Its under System-->Preferences-->Keyboard-->Layouts-->Add-->Language (for example, US English)-->Dvorak.

just a little hidden.

---

### Post by samx on 2005-12-03
Another alternative would be writing your own layout. I'm using this method because I have a special (German) dvorak layout with some personal changes.
It's really easy with xmodmap:
```

xmodmap -pke > ~/.xmodmap.normal
cp ~/.xmodmap.normal ~/.xmodmap.special
vim ~./xmodmap.special
```
Now you can add all modifications at the bottom of this file. A sample line would be
```
keysym d = e E EuroSign
```
After you added alle modifications, you can easily switch between the layouts by adding aliases to your /etc/bash.bashrc
```
alias 1="xmodmap ~/.xmodmap.normal"
alias 2="xmodmap ~/.xmodmap.special"
```
This method is useful if you have your own special layout or if sometimes "normal" people want to type at your pc, you can switch layouts just by typing 1 or 2 into a konsole (and you don't have to know which layout is active at the moment)

---

### Post by akimmell on 2006-07-09
How do you switch to it once you've enabled it?

---

