---
title: "[SOLVED] Middle clicking loads clipboard contents in Firefox's address bar"
date: 2008-08-15
forum: General Help
---

### Post by feedmecereal on 2008-08-15
I've had this problem probably ever since I upgraded to 8.04 but it has really started to bother me now.

Let's say that I have some text copied in the clipboard, maybe "example." I then attempt to load a link on the page by middle clicking but I accidentally click on an empty spot on the page. Firefox will open a new tab with the address [www.example.com](www.example.com).

How do I stop this behavior?

---

### Post by picpak on 2008-08-15
What you can do is go to about:config in your address bar, filter by "middlemouse" and set "middlemouse.contentLoadURL" to false. That should disable it for you. :)

---

