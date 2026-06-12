---
title: "Compiz Woes!"
date: 2008-11-27
forum: General Help
---

### Post by lkc0987 on 2008-11-27
hi,

I noticed that compiz was crashing on me ever so often with the SEGMENTATION ERROR. so i ran compiz through the terminal and sometimes i got some errors as 

> Invalid WM_TRANSIENT_FOR window <> specified for <> ()

i was then tryin to go through all the things i had done before i started gettin this problem, and i felt that AWN was causing all the problems.

i get this message for one

> Invalid WM_TRANSIENT_FOR window <> specified for <> (awn_elemen)

this was with awn trunk i guess...coz i never had problems with the awn package before.this was the first time that i had tried the trunk(i donno what the diff between them is!)

so...any bright ideas?!

---

### Post by lkc0987 on 2008-11-28
Yep..

i guess i solved the problem..

there is a problem with awn-trunk and compiz...

i reverted back to awn and everything works perfect...

---

