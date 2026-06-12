---
title: "firebox problem"
date: 2008-07-25
forum: General Help
---

### Post by minhdinh on 2008-07-25
when im using firefox and i press the backspace button on my computer it doesnt go back to previous pages like when im using internet explorer. i want to know wat i have to do to make the backspace button go to previous page in firefox. i need step by step instructions please im a noob.


another problem. i want to make it so the first click on the address bar highlights everything so i can quicky erase and type a new adress in like in internet explorer. please tell me how to do that too

---

### Post by aktiwers on 2008-07-25
In Firefox, type:
```
about:config
```

Then search for:
```
browser.backspace_action
```

Double-click it and set the value to "0".

Maybe you need to restart Firefox to make the changes take effect.

---

### Post by minhdinh on 2008-07-25
thanks that worked but wat about my other problem. how do i make it so i highlight everything in the adress bar with the first click

---

### Post by aktiwers on 2008-07-25
Sorry I didnt see that. I don't know how to do that, but you could use CTRL+L.

---

### Post by BlitheB on 2008-07-26
For selecting all text in Firefox's address bar, use the same steps above, but filter instead for:

browser.urlbar.clickSelectsAll

double click on the entry to set it from its default of false to true.

---

### Post by minhdinh on 2008-07-29
thanks alot for the help that worked

---

