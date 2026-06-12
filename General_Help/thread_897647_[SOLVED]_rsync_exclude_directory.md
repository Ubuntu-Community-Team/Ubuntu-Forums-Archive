---
title: "[SOLVED] rsync: exclude directory"
date: 2008-08-22
forum: General Help
---

### Post by x1a4 on 2008-08-22
Hi,
To exclude a directory from sync'ing using rsync, should I use 
--exclude=dir
or
--exclude=dir/
or does it matter?

Thank you.

---

### Post by rjack on 2008-08-22
--exclude=dir

When you're in doubt run rsync with the -n (--dry-run) option, so you can see what it would do.

---

