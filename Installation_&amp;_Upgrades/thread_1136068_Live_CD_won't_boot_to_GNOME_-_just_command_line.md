---
title: "Live CD won't boot to GNOME - just command line"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2009-04-24
Hi there,

after being badly burned by the 7.10->8.04 upgrade (I lost my xorg config and had to call in an expert to fix it - I'm a Windows expert Linux noob) I decided to just see how 9.04 looks. The live CD boots fine, I get the menu. I select "try Ubuntu without installing" option, it loads and goes straight to the command line.

no GNOME.

no GUI

a command line.

since no one else appears to have this, it's clearly my setup. Could my nvidia graphics card (which caused all the problems last time) be the culprit ? Or have I done something so staggeringly stupid, I'll just have to die ?

cheers guys

---

### Post by Monotoko on 2009-04-24
odd, can you run ```
lspci
``` and display the results here?

also try running startx from the command line...im pretty sure it wont start, but it will probably give some meaningful errors as to why it doesnt start

---

### Post by ddrichardson on 2009-04-24
I don't know how much the LiveCD logs but are there any clues in /var/log/Xorg.0.log?

---

### Post by Jethro_uk on 2009-04-24
> **Monotoko said:**
> odd, can you run ```
lspci
``` and display the results here?

also try running startx from the command line...im pretty sure it wont start, but it will probably give some meaningful errors as to why it doesnt start

unfortunately the machine I am writing on now is the one I am trying it on ... I may try once more before bed....

---

### Post by Jethro_uk on 2009-04-25
> **Monotoko said:**
> odd, can you run ```
lspci
``` and display the results here?

also try running startx from the command line...im pretty sure it wont start, but it will probably give some meaningful errors as to why it doesnt start

startx worked fine  ! New version looks nice, but until I can find an expert to install it, I'm sticking with 8.04

---

