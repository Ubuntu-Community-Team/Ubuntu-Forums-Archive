---
title: "[SOLVED] Backspace for last page in FireFox"
date: 2008-09-12
forum: General Help
---

### Post by kokkus on 2008-09-12
An option I remember I liked alot when I used windows is that I could go back to the last page by using backspace.
Is there any way I can add that option in firefox on ubuntu?
ANy plugins, addons or scripts or whatever? 

Thanks:)

---

### Post by prshah on 2008-09-12
> **kokkus said:**
> is that I could go back to the last page by using backspace.
Is there any way I can add that option in firefox on ubuntu?


Open a fresh tab, and put the below address into the address bar:```
about:config
```, Then, in the filter bar, type in ```
backspace
``` and you should find an option "browser.backspace_action"; set it to "0" (or play about with the setting). The change will take effect immediately.

---

### Post by kokkus on 2008-09-12
OK thank you so much. I figured it out now :)

---

