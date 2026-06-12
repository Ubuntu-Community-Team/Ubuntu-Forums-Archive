---
title: "How to handle paths with spaces in nautilus-actions?"
date: 2008-11-11
forum: General Help
---

### Post by reader4 on 2008-11-11
I have several shell scripts that I use with nautilus-actions, but they fail when the file path contains a space and multiple files are used.  Is there any way to pass/receive multiple path names correctly?

I can either pass as '%M' from nautilus-actions or receive as "'$@'" in the script, but this only quotes the whole list: 
```
'/home/user/test dir/test.file.1 /home/user/test dir/test.file.2'

```
rather than the preferred:
```
'/home/user/test dir/test.file.1' '/home/user/test dir/test.file.2'

```
Help?

---

