---
title: "Renaming bulk files"
date: 2008-11-17
forum: General Help
---

### Post by lerrup on 2008-11-17
I need help with some basic bash help.

I need to change the names of a whole load of files which are named eg _1000221.JPG, to take off the first _ to be 1000221.JPG.

Now this should be possible, but I don't have a clue. Can anyone help?

---

### Post by kaibob on 2008-11-17
> **lerrup said:**
> ...I need to change the names of a whole load of files which are named eg _1000221.JPG, to take off the first _ to be 1000221.JPG....

There are many ways to do this. The following command line entered in a terminal window works:

```
for FILE in *.JPG ; do mv "$FILE" "${FILE/#_/}" ; done
```

BTW, I assume that eg means for example and is not a part of the file name. Also, try this with some test files first.

---

