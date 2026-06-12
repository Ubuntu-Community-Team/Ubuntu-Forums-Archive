---
title: "gnucash failing because of font"
date: 2005-11-28
forum: General Help
---

### Post by kamika on 2005-11-28
i recently installed gnucash only to find it crashing when starting

```
kamika@fuzzbox:~$ gnucash
Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*
```

i did a google search but none of the hints helped.
is there a way of just installing that specific font?

thanks.

ubuntu 5.10 amd64

excuse me, wrong forum, can somebody please move to 5.10, i'm really sorry!

---

### Post by apollyonis on 2005-11-30
Try this:

```
sudo apt-get install cl-pdf
```

That will install the adobe-helvectica fonts under /usr/share/fonts/afms/adobe

---

### Post by IanLowe on 2005-12-04
Don't know if it helped the OP, but I'm having the same error, and it didn't resolve it for me... :(

ah well - the hunt continues :)

---

