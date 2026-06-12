---
title: "FF 1.5 won't install extensions"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2005-12-30
Can't install extensions for my FF 1.5 installation. Although haVE INSTAlled a ton of them in the past. Have also tried running FF1.5 extensioles w/root but I still cant install them

When I click on an XPI it just says where to I want to save it. 
How to fix this?

---

### Post by d11wtq on 2005-12-30
Odd... sounds like it doesn't know how to handle the xpi mime type :?

Try deleting the ~/.mozilla directory and give it another shot :)

NOTE: You'll lose all personal settings (bookmarks etc) if you do that so you might want to make a backup first.

---

### Post by ashrack on 2005-12-30
Weird. Lunched "gksu firefox" and then exited. And lunched it again without "su" priviligies and now it works fine.
Any1 knows why?

---

