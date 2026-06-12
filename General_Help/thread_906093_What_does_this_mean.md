---
title: "What does this mean?"
date: 2008-08-31
forum: General Help
---

### Post by junojpeg on 2008-08-31
I tried to install this software so that I could install hsfmodem for my dial-up connection, but this message popped up. What does it mean?

---

### Post by Comzee on 2008-08-31
It most likely means you need "libc6-dev". Go into your package manager and search for that exact dependency and see of it there, if it is download and install it.

---

### Post by Jungle-Cat on 2008-08-31
Since it is 'unsatisfiable'... this most likely means that it is not in the repos. You will have to find a deb package for it, or find another way to install the dependancy.

---

### Post by nikgare on 2008-08-31
You can probably get it here:
[https://launchpad.net/ubuntu/hardy/i386/libc6-dev](https://launchpad.net/ubuntu/hardy/i386/libc6-dev)

---

