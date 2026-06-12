---
title: "Reinstall 8.10 without removing /home on separate partition"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by wanted-66 on 2009-02-25
I need to do a reinstall of Ubuntu 8.10. Last time I used manual partitioning and have the /home folder on its own partition. How do I reinstall and use the original home partition without destroying it? 
Remove swap partition and / partition and reformat install them as before? Do I have to specify a /home partition like last time?
Thanks in advance for any advice

---

### Post by taurus on 2009-02-25
Yes, just mount the right partition to /home but do not format it.  Then, you can create the same username so you would use the same $HOME when it's finished.

---

### Post by wanted-66 on 2009-02-25
Thanks so much. Followed your instructions- worked perfectly. I've learned a lot in the last few months- my husband thinks I'm slightly crazy!

---

### Post by taurus on 2009-02-25
Crazy like a fox!

---

