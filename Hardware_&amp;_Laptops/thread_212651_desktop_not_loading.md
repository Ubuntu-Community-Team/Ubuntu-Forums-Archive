---
title: "desktop not loading"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by davebradford on 2006-07-10
i have just installed ubuntu on an older laptop of mine.. was working well and now for some reason i cannot get a desktop.. i log in then i get a cursor and nothing! not even a splash screen! stays like that so i have to perform an control-alt-backspace reload x and then change desktop session to failsafe? any ideas? laptop specs are the following:

Celeron 1.2Ghz
256 Ram
S3 Graphics Card - Shared 32 MB

little help! thx

---

### Post by bigken on 2006-07-10
you could try *sudo apt-get install ubuntu-desktop* in a terminal and see if this fixes it ;)

---

### Post by davebradford on 2006-07-10
will that work even if i've got the packages installed already? i though it wud prob come up saying you already have these installed?

---

### Post by Tux+ on 2006-07-10
what does it say in the x log? should be in /var/log/Xorg.n.log

where "n" is the display number (usually 0 by default)

---

### Post by davebradford on 2006-07-10
there is no log in that specified folder? any other ideas?

---

