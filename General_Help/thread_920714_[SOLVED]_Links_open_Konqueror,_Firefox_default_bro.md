---
title: "[SOLVED] Links open Konqueror, Firefox default browser"
date: 2008-09-15
forum: General Help
---

### Post by hwttdz on 2008-09-15
When I click a link, specifically from a pidgin conversation Konqueror opens, despite Firefox being my default browser, any ideas on how to fix?

Note when in firefox I did preferences advanced, "check now" for default browserness it said it was.  However when I did.

sudo update-alternatives --config x-www-browser

it said it wasn't and I was able to select firefox.  Behavior is now fixed.

---

### Post by prince_niceguy on 2008-09-15
It depends on lot of configs esp if you mix up kde and gtk apps. They have different files for referring the default browsers. Some how it seems KDE overwrites the preferences of gnome, not sure. Happened to me too. I changed the preferences in kconrol and it worked perfectly fin after that.

---

