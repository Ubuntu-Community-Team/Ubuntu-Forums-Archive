---
title: "delete first 3charachters of file sed or awk"
date: 2008-08-28
forum: General Help
---

### Post by dapim on 2008-08-28
i wanna delete just the 3 first carachters of this file,
 
i try sed but it only didn't find a way of doing it

sed  '^3//d'

file

asdffsd
sdfgdhd
hdfhdhd

---

### Post by squaregoldfish on 2008-08-28
Try this:

```
sed -i 's/^...//' file
```

The -i allows inline editing of the file. The . will find any character, so three of them will find three characters.

This won't work if the file has less than three characters in it, because it explicitly looks for three characters - if it doesn't find them, it won't delete them.

If this is going to be a problem, let me know and I'll see what I can come up with.

Steve.

---

