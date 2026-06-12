---
title: "Japanese input (hiragana, katakana, kanji) in an English environment"
date: 2008-11-04
forum: General Help
---

### Post by Cifra on 2008-11-04
Hi guys, I would like to keep my Gnome English while being able to input Japanese Kana characters. there is a good tutorial on the wiki, but I have to edit a few lines in 
```
gksudo gedit /etc/X11/Xsession.d/74custom-scim_startup
```

When I open this file, it's empty so I don't believe it's gonna help.

Anyone of you know how to do it? I already installed Japanese language support, but I don't know where to select and find the keyboard conevrter to kana characters.

---

### Post by ShadowWraith on 2008-11-04
Try installing SCIM using Synaptic. Then just go into terminal and type "scim". It'll start up, and you'll be able to emulate tons of languages, including Japanese.

---

### Post by Cifra on 2008-11-04
OK, I'll try that but shoudn't there be a more accessible, GUI way? :)

---

### Post by ryukent on 2008-11-09
The "gksudo gedit /etc/X11/Xsession.d/74custom-scim_startup" script was needed a long time ago. Recent versions of Ubuntu should not require it. Please see my other thread on installing Japanese for English ubuntu:

[http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)

---

