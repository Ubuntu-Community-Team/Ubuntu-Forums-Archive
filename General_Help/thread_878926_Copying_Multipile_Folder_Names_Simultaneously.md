---
title: "Copying Multipile Folder Names Simultaneously"
date: 2008-08-03
forum: General Help
---

### Post by nirvana21 on 2008-08-03
I have a folder filled with many, many folders. I would like to list the names of these folders without copying each one individually. I want to be able to paste them in an open office document or something.

Any help is appreciated!

---

### Post by prshah on 2008-08-03
> **nirvana21 said:**
> I have a folder filled with many, many folders. I would like to list the names of these folders without copying each one individually. I want to be able to paste them in an open office document or something.

Any help is appreciated!

You need the tree utility: Open a terminal (Applications-Accessories-Terminal) and give the commands
```
sudo apt-get install tree
tree -d /path/to/folder
```

Or if you prefer to do it without tree, and dont mind a slightly messy output, you can use ```
 ls -R --file-type /path/to/folder | grep "/"

```

You can redirect the output of either of these commands to a file called folderlist by appending "> ~/folderlist", eg:```
tree -d /path/to/folder > ~/folderlist
``` The "folderlist" file will be created in your home directory.

---

