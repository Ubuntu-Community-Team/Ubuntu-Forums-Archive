---
title: "3d cards and WoW"
date: 2009-06-13
forum: Hardware
---

### Post by miggerish on 2009-06-13
So before I buy a game called World of Warcraft, I am trying to figure out if it will work on my computer.  One of the things I need to find out is which 3d card I have and if it can support WoW.

here is the list of supported ones: [http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21085](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21085)

can someone help me find out?

---

### Post by cariboo on 2009-06-13
If you aren't sure what video card you system has, open an Applications-->Accessories--Terminal and type:

```
lspci | grep VGA
```

This should show a listing that looks something like this:

```
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```

Then check with the page you linked to.

---

