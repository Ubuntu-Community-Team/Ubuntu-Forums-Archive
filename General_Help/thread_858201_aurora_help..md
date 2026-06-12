---
title: "aurora help."
date: 2008-07-13
forum: General Help
---

### Post by davbren on 2008-07-13
hi, I've installed aurora and its themes, I've been playing with the config files to try and get everything blended in. unfortunately I can't quite get it rite, could someone help me out please?

---

### Post by spupy on 2008-07-14
Hi, I guess you want to make the toolbar blend better with the rest of the window? Unfortunately, this is not possible by just altering gtkrc. This is programmed in the aurora theme by default. I changed the source of the theme and now it blends. I attach the new source. Extract it end then run:
```
./configure --enable-animation
make
sudo make install
```
Before doing the last step, make sure to switch to another theme, otherwise your programs will crash. (because if they are using aurora while your change aurora, bad things happen :) )
Hope this helps.

EDIT: Of course, you still have to alter the colors in the gtkrc file, to match the color of the toolbar gradient with the color of the window titlebar.

---

### Post by davbren on 2008-07-14
Hey thanx for the help but wen I try to configure it it says 

Configure: error: GTK+_2.10 is required to compile aurora

it does't let me get any further...

---

### Post by spupy on 2008-07-14
> **davbren said:**
> Hey thanx for the help but wen I try to configure it it says 

Configure: error: GTK+_2.10 is required to compile aurora

it does't let me get any further...


What Ubuntu are you using? Try without "--enable-animation".

---

### Post by lusepuster on 2008-08-17
Have you tried ```
apt-get build-depend gtk-engine-[pick one here]
```... You probably need the developer headers of GTK to build the engine.

---

