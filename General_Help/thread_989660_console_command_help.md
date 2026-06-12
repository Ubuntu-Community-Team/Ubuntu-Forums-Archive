---
title: "console command help"
date: 2008-11-21
forum: General Help
---

### Post by zebulon M on 2008-11-21
I wanna save part of a large text file to another file. The lines 25000 to 10000000 of 'input.txt' should be written to 'output.txt' . Would someone like to help me with the proper command?

---

### Post by lswb on 2008-11-21
> **zebulon M said:**
> I wanna save part of a large text file to another file. The lines 25000 to 10000000 of 'input.txt' should be written to 'output.txt' . Would someone like to help me with the proper command?

sed -n '25000,10000000p' input.txt>output.txt

should do it.

---

