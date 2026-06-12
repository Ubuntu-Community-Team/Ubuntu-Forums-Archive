---
title: "JavaScript Problem in Firefox 3"
date: 2008-07-10
forum: General Help
---

### Post by TrasMontano on 2008-07-10
Since i upgraded to ubuntu 8.04.1 i have a problems with firefox 3.
Usually when i load a new page in firefox 3 a small window apears and on the top it says "Aplicação JavaScript" (JavaScript Aplication) and then in the middle is says: TypeError:doc.locations is null"
Normalll, after clicking "ok" it loads the page; but if the page has images ou loads videos, the firefox crushes completlly.

After this, when i restart firefox, if i choose to load back the pages that were open before the crash, everything goes back to normal and works fine.

What can i do to fixe this?

---

### Post by Pablo89 on 2008-07-10
Try to move your "~/.mozilla" directory somewhere else for a moment and check if firefox still has such problems, used without your configuration. It seems like something really strange in your profile settings (e. g. like an effect of some buggy add-on), more likely than something into the firefox installation (if the problem keeps appearing, you can also reinstall firefox packages...).

---

### Post by TrasMontano on 2008-07-11
I' ve tried moving, and uninstalled, reinstalled and even done a fresh install and nothing.
From what i' ve read on the forum, i guess i have two troblems: a flash problem that crashes firefox and a plugin problem, this because a tried disableing my plugins and discovered that it was the "neogame" for firefox 3 that was causing some kind of problem with javascript...

Any idea??

---

### Post by p@rky on 2008-09-23
have the same issue it is definitely javascript related any ideas out there?

---

### Post by Vectrox on 2008-10-13
Its a Firefox related bug, it also happens in Windows XP.

---

### Post by Thomas00 on 2008-12-29
"Ya of course every single computer can be affected with virus, virus can enter to your computer through e-mails, pen drive's and network connection's. The [www.search-and-destroy.com](www.search-and-destroy.com) is ready to fight with any kind of virus i think everyone should try this anti virus software.


Thank You."

---

### Post by pirog on 2010-02-06
hi, it is an old thread I know but the problem occurred in Karmic too.

I deleted contents (just a single file) in the ./mozilla/firefox/gdfgd.default/OfflineCache and JS started working again.

I hope it helps.

---

