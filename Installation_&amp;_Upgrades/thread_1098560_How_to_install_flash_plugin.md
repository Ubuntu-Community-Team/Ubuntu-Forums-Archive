---
title: "How to install flash plugin"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by Odolyte on 2009-03-17
Hi Everyone,

I've figured out by myself a simpple way to install the flash player plugin for my firefox browser, so i post the solution because i didn't find anything SIMPLE ! I made this on ubuntu 8.10 but i gess that would work with other versions.

Firts launch a terminal in your Applications > Utilities (or accessories).

Then type : sudo synaptic
this will launch the synaptic package manager giving it the rights to install packages.

Enter your user password.

Then in the search field type "flash"

You will see a flashplugin-nonfree item > check the item

A popup window will ask if you accept to install dependent packages
> Accept the install.

When it's finished, close your browser, then restart it and... tada... you have your flash plugin !!

Hope than will help other beginners like me...

Odo.

---

### Post by taurus on 2009-03-17
1.  Synaptic is in System -> Administration -> Synaptic Package Manager so no need to type anything in a terminal (Applications -> Accessories -> Terminal) unless it doesn't run from there.  Then, you would run it from a terminal to see what's wrong with it.  And by the way, it should be **gksudo synaptic**.

2.  If you want the plugins, just install ubuntu-restricted-extras package and you would have java, flash, codecs, fonts, etc.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

