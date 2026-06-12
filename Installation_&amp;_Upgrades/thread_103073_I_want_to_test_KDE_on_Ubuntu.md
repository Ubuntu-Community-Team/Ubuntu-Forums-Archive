---
title: "I want to test KDE on Ubuntu"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by dguido on 2005-12-13
Can I apt-get install kde-desktop over my regular Gnome Ubuntu desktop and just choose the window manager I want at login in gdm?  Or is that going to cause major problems?  How does one handle switching between these two huge window managers in Ubuntu?

---

### Post by linbetwin on 2005-12-13
the package is called "kubuntu-desktop".
Or you can instal "kde", if you want all of KDE.

---

### Post by teaker1s on 2005-12-13
just install kubuntu desktop or if you install kde you will be asked if you want gnome or kde login manager

---

### Post by dguido on 2005-12-13
[QUOTE=teaker1s]just install kubuntu desktop or if you install kde you will be asked if you want gnome or kde login manager[/QUOTE]

Wait... this is what I was asking about, I just made a typo on kubuntu-desktop.  Will installing kubuntu-desktop remove any packages from ubuntu-desktop?  Can they coexist?  Or do I have to install just 'kde'.  Please explain in a little more detail? :-)

---

### Post by linbetwin on 2005-12-13
[quote=teaker1s]just install kubuntu desktop or if you install kde you will be asked if you want gnome or kde login manager[/quote]

That sentence can be deceiving without punctuation.

---

### Post by aysiu on 2005-12-13
[QUOTE=dguido]Will installing kubuntu-desktop remove any packages from ubuntu-desktop?[/quote] No.  

> Can they coexist? Yes.  

> Or do I have to install just 'kde'.  Please explain in a little more detail? :-) KDE is a different set of packages from kubuntu-desktop.

---

### Post by teaker1s on 2005-12-13
Sorry my puntuation is terrible, If you install kubuntu you will have less duplicate 
programs.
installing KDE will give you the full works and you will find some kde programs that do the same as a gnome one.

---

### Post by Concrete on 2006-08-13
How can I up-grade my ubuntu whit gnome to kde & gnome?
From where to install KDE desktop?

---

### Post by linear on 2006-08-13
In a terminal window, type:

[B]sudo aptitude install kubuntu-desktop
[/B]
Why aptitude? If you change your mind, you can easily remove everything with:

**sudo aptitude remove kubuntu-desktop**

---

