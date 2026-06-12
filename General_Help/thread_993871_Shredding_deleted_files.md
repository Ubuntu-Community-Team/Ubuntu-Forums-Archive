---
title: "Shredding deleted files"
date: 2008-11-26
forum: General Help
---

### Post by change_mode on 2008-11-26
What's the best thing to do if you deleted files that you should have shredded? 
Is there something like a tool that overwrites all empty space with 0s?

---

### Post by iKonaK on 2008-11-26
First of all it's almost imposible to recover files from ext3, as far as i heard it's possible but it's a pain in the as. As for shredding try the shred command, see "man shred" for more info :)

---

### Post by change_mode on 2008-11-26
I got to know about the shred command right after I deleted the files... bad timing. 
It's only a credit card number though, so not a big deal. I'm just curious if it's possible :)

---

### Post by iKonaK on 2008-11-26
...you can copy several files in the empty space and then shred them, but will take a long time and wouldn help much too much.

---

