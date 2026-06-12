---
title: "breezy + swiss-german keyboard"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by billybear on 2005-10-10
Hi!
I'm trying the new amazing ubuntu which give me only one problem:
I've a Microsoft Media Pro keyboard with a swiss-german layout and I've the qwertzu keys but the Alt + other doesn't work (so I couldn't have the "at" and others useful keys like accents).
Does somebody knows how to solve this?

-- 
Julien

---

### Post by rwabel on 2005-10-11
[quote=billybear]Hi!
I'm trying the new amazing ubuntu which give me only one problem:
I've a Microsoft Media Pro keyboard with a swiss-german layout and I've the qwertzu keys but the Alt + other doesn't work (so I couldn't have the "at" and others useful keys like accents).
Does somebody knows how to solve this?

-- 
Julien[/quote]

How does your xorg.conf file look like?
For me swiss german is working fine:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ch"
        Option          "XkbVariant"    "de"
EndSection

```

do you have the problem in your window manager? does it work when you change back to the console mode (ctrl-alt-f1)?

---

