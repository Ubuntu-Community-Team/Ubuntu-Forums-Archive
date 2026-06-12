---
title: "[SOLVED] Firefox update and lost swedish language"
date: 2008-10-12
forum: General Help
---

### Post by axelsvag on 2008-10-12
After the last update my swedish language in firefox (Mozilla/5.0 (X11; U; Linux i686; sv-SE; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3) was lost. Does anyone have a fix for this?

---

### Post by Tamlynmac on 2008-10-12
Have you checked:

firefox/edit/preferences/content tab/languages/choose/select a language to add/select swedish/add button

Highlight swedish and use the move up button to move to top - assuring priority.

---

### Post by axelsvag on 2008-10-13
Thank you for the answer. I tried your advice and all looked fine. When I look at the problem I really think that it is the gnome -language pack that was updated. Maybe the connection between the gnome package and firefox is not perfect.? Skould I activate the backports to get a fast fix?

---

### Post by Tamlynmac on 2008-10-13
Hopefully, someone else will respond to that question. I'm not certain thats the best solution...

---

### Post by andeol on 2008-10-18
There are lots of bug reports on this, search for firefox and language pack in the bug tracker. This affects all languages, I'm guessing there will be an update with a fix if you can wait. Else search the reports for quick fixes.

---

### Post by axelsvag on 2008-12-19
Most of the swedish language support seems to be back after the last update so I consider the problem solved.

---

### Post by sundman on 2009-06-24
It seems that updates to firefox and language packs are sometimes applied in the wrong order (e.g. [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/195013](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/195013)) reverting firefox to English.

Reinstalling the base language pack can solve this issue e.g.:

```
sudo apt-get install --reinstall language-pack-sv-base
```

---

