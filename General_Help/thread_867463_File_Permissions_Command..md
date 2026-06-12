---
title: "File Permissions Command."
date: 2008-07-22
forum: General Help
---

### Post by davidshq on 2008-07-22
I have a bunch of files that don't have Write permissions for the group they are associated in. They are across a lot of different directories. I want to keep all of their other permissions the same and only add write permissions for group. How can I do this? I'm operating at the CLI.
David.

---

### Post by pdwerryhouse on 2008-07-22
The command you want is:

```
chmod g+w *filename*
```

If you want to do this across a lot of files with the same group, in different directories, then use:

```
find . -group *groupname* -exec chmod g+w '{}' \;
```

WARNING! Make sure you know what you're doing before running the command above.

---

