---
title: "How to keep an external HDD asleep?"
date: 2008-09-04
forum: General Help
---

### Post by wfriesen on 2008-09-04
I am running Hardy Heron. I have a Maxtor external HDD, and after 10 or 15 minutes of not being accessed, it goes into a kind of "sleep" mode, and to access it again it takes a second or two to wake it up.

This is fine, except that sometimes when I open nautilus to my home folder, for some reason the hdd wakes itself up and I have to wait those couple of seconds before nautilus will open.

How can I stop this from happening?

---

### Post by wfriesen on 2008-09-08
Well, in System->Preferences->Search and Indexing, under "Ignored Files" I added /media/disk which is where the HDD gets mounted to.

So far it seems to have done the trick.

---

