---
title: "[SOLVED] Make a list over my programs?"
date: 2008-07-24
forum: General Help
---

### Post by Wikzo on 2008-07-24
When I upgraded from Ubuntu 7.10 to 8.04 with a separate Home partition, I lost a lot of my programs. They weren't installed in my Home folder, so I had to install them all over again.

The problem was that I hardly was able to remember all my applications, so I decided to start making a list over my programs to use for the future. But isn't there an easier way, like a program that makes a list with ALL your programs?

---

### Post by Potatoj316 on 2008-07-24
You might be able to use aptitude to list all of your installed packages but that is a very long list.  Many packages are installed because they are needed by others, you wouldnt install them all manually.  Maybe if you use the add/remove programs thing (not synaptic) you can tell it to only display installed programs.

---

### Post by Wikzo on 2008-07-24
Basically, I want a list over the programs stored in "Programs" in the top left corner. In Windows, I once took a screenshot of that menu, but in GNOME it has a lot of different categories like "Internet", "Office", "Games" etc.

---

### Post by Yannick Le Saint kyncani on 2008-07-24
> **Wikzo said:**
> But isn't there an easier way, like a program that makes a list with ALL your programs?

I personnally keep a list of all programs I want, but debfoster and deborphans can help you generate such list if you don't have one. There is also dpkg -l which can give you a list of all installed packages.

---

### Post by Potatoj316 on 2008-07-24
Yeah, dpkg -l will list the installed packages, but its probably a long list, you might not be able to fit it all in your terminal at once, to fix that use this
```
dpkg -l | more
```
the | is the vertical line that is above the enter key

---

### Post by louieb on 2008-07-24
:lolflag:Because its Linux **less** is actually more that **more**. 
```
dpkg -l | less
```

With less the arrow keys scroll up and down and the page up / page down keys actually page up and down. 

Or you could redirect the output to a file in your home folder

```
dpkg -l >  ~/dpkg.txt
```

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by nick_h on 2008-07-24
Here is a useful link which describes how to save a list of packages and restore it on another installation.

[http://wiki.debian.org/Packaging/Listing_Installed_Packages](http://wiki.debian.org/Packaging/Listing_Installed_Packages)

---

### Post by Wikzo on 2008-07-25
Thank you very much.

---

