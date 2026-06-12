---
title: "[SOLVED] How to list files only with numbers in directory?"
date: 2008-08-13
forum: General Help
---

### Post by abcuser on 2008-08-13
Hi,
in Ubuntu 8.04 I would like to list all files in currect directory that follows the following rules:
1. first character is D and
2. on second to fourth has numbers and
3. fifth character is underscore.

I have the following files in directory:
D001_some_text.txt
Dabc_some_text.txt

So far I have written: ls D???_*.txt but this is only for first and third rule. How to apply second rule?
Thanks,
Abcuser

---

### Post by Mad-Halfling on 2008-08-13
Have a poke around with regular expressions, there's plenty of stuff in there.  Have only done bits with them, so I'm sure there's a more efficient way of writing it, but
ls D[0-9][0-9][0-9]_*.txt
will work.

---

