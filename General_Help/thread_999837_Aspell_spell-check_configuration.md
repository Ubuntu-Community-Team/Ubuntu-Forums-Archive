---
title: "Aspell spell-check configuration"
date: 2008-12-02
forum: General Help
---

### Post by Oceanic on 2008-12-02
Hello all !  Spelling check not working !

In Feisty the spellchecker (Aspell) fortunately ignored the HTML tags when checking a HTML file in Kate or Kwrite. 
Now in Intrepid, the spell checking start with !DOCTYPE, which obviously isn't proper English :-) It checks everything, which makes aspell unusable really.


```
man aspell
```
```
aspell help
```

shows that it is possible to filter for HTML files via
a) ignore tags
b) but force the check of certain attributes  (alt, title, etc)

```
aspell dump config
```
states that the config file is /etc/aspell.config  
yet there is NO aspell.config (hidden or not) on my system...

**Question 1)**
Where can i alter the aspell settings?

**Question 2)**
How can i add a lot of HTML tags (which are then to be ignored)
and how can i add a few Attributes to include...?

Thanks in advance !!! ):P


Not very good with command line - usually mess things up...

---

### Post by Oceanic on 2008-12-03
Anyone... please

---

### Post by Oceanic on 2008-12-08
Please...
anyone?
Cheers :-)

---

### Post by editrix on 2008-12-08
I didn't read all the documentation at [http://aspell.net/](http://aspell.net/) but sometimes it's just a question of creating an empty file named aspell.config.

> Not very good with command line - usually mess things up...

Me too. I'd just copy/paste everything into OpenOffice and spellcheck from there.

---

