---
title: "Mozilla forgot passwords"
date: 2008-07-11
forum: General Help
---

### Post by trent_shipley on 2008-07-11
I believe that after a recent Ubuntu upgrade of Firefox, Firefox forgot its assigned homepage and password list.  It still remembers its bookmarks and user names and field completions for forms.

I would write a Firefox list about this issue but I believe it was related to a recent Ubuntu Hardy patch or upgrade of Firefox.  I also suspect the homepage and password files are hanging around somewhere and would work again if I could just point Firefox to them.

---

### Post by josef.sabl on 2008-09-25
This happened for me today when I updated Firefox. All passwords are lost and FF does not offer storing them when I enter them again.

---

### Post by rklk on 2008-09-25
josef.sabl, it's a bug tracked here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270429](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270429)
I found a workaround for this here: [https://bugzilla.mozilla.org/show_bug.cgi?id=454708](https://bugzilla.mozilla.org/show_bug.cgi?id=454708)

Just open your **/home/<username>/.mozilla/firefox/<profile>.default/signons3.txt** file in gedit. **File->Save as** and overwrite the file, but change the encoding to **UTF-8**. All passwords should be back.

---

