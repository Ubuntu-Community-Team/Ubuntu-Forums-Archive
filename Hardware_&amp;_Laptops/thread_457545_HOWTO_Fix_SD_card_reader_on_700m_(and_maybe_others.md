---
title: "HOWTO: Fix SD card reader on 700m (and maybe others)"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by outphase on 2007-05-28
I searched for this and couldn't find an answer, but after careful googling for a while, I found a solution. Credit goes to someone else as I am just relaying the answer. I couldn't figure out why it wouldn't work when everything else did, but these lines helped.

```
sudo gedit /etc/modules
```

Then add the following to the list
```
tifm_7xx1
tifm_core
tifm_sd
```

After a reboot, you should have the SD reader working. If anyone has any alternatives, post them here.

---

### Post by 56phil on 2007-05-30
Thanks! This fix worked on my Gateway M680.

---

### Post by Lutin on 2007-05-31
This also works on the Acer Aspire 7003 laptop.:p Again I found the instructions after a Google search. All credit to whoever posted the solution originally.

---

### Post by carlthewinner on 2008-01-29
I did this on my 700m ubuntu 7.10, the card reader works, but erratically ejects itself. Has anyone found a solution for this?  (It won't even work with my USB multi flashcard drive.)

---

