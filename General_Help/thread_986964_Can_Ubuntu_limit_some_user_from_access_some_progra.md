---
title: "Can Ubuntu limit some user from access some program?"
date: 2008-11-19
forum: General Help
---

### Post by asaren on 2008-11-19
Can Ubuntu limit some user from access some program? like firefox?

Thank you

---

### Post by Martje_001 on 2008-11-19
Hmm, yes it can. But it requires some tweaking. In big steps:

1) Create a group called firefox
2) chown name-of-administrator:firefox /usr/bin/firefox
3) Go with nautilus to /usr/bin and set firefox permissions.

I know it sounds a little bit confusing, but just try it! ;)

---

