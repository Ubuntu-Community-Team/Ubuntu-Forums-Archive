---
title: "Can't add bookmarks in firefox"
date: 2005-11-22
forum: General Help
---

### Post by sawjew on 2005-11-22
I can't add new bookmarks to firefox.  When I right click and add bookmark or from the bookmarks menu or using cntrl+D
 no bookmark is added.  nothing happens at all.  Does anyone have any ideas of how to fix this as it is rather frustrating.

Thanks.

I fixed the problem by uninstalling the bookmarks duplicate detector extension, it now works fine.:oops:

---

### Post by houseofmore on 2005-11-23
have you checked the permissions on your firefox folder?

`chown -R username .mozilla` may help...

---

### Post by PenguinZdravko on 2005-11-23
I had the same problem, changing the permissions works.

---

