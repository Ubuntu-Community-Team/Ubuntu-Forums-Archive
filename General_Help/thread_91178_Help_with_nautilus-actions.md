---
title: "Help with nautilus-actions"
date: 2005-11-16
forum: General Help
---

### Post by zoulman on 2005-11-16
Has anyone managed to get nautilus-actions working on breezy - I have actually managed to install it but when I add new actions they never show up in the context menus. Please help, oh wo is me.

---

### Post by zoulman on 2005-11-17
bump

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-11-17
A Deb is avalible at
[http://www.grumz.net/index.php?q=taxonomy/term/6/9](http://www.grumz.net/index.php?q=taxonomy/term/6/9)

you might need to restart nautilus after editing

```
nautilus -q
```

You need to with sudo to edit system wide commands

NOTE: Dont forget to check the right boxs at the bottom of the edit screen "Appears if sceme in this list" else your command will never appear :)

---

### Post by magnusbb on 2005-11-17
I am just curious, what is actually the purpose of **nautilus-actions**?

I know of nautilus-scripts, but not this.

---

### Post by GrumZ on 2005-11-18
The purpose of nautilus-actions is quite the same as nautilus-scripts, but the difference is that the actions/scripts appears in a contextual manner with nautilus-actions. 

For example if you make a script to convert wav file into ogg files, it will never appears when you select a PDF or JPEG file, but only when you select a WAV file.

Let's check this page [http://www.grumz.net/taxonomy/term/4/9](http://www.grumz.net/taxonomy/term/4/9) for the details ;) 

zoulman, is your problem solved ?

GrumZ
--
[http://www.grumz.net/](http://www.grumz.net/)

---

