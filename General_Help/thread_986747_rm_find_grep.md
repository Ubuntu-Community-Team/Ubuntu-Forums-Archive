---
title: "rm find grep"
date: 2008-11-18
forum: General Help
---

### Post by HuXu on 2008-11-18
I have searched my brains out tried different find grep combinations and none of them work...

Im trying to delete all the .m4p and .m4a files from my Music directory.  But leave all the rest alone.

---

### Post by dsauxier on 2008-11-18
Before running the destructive command, I like to see what I'm deleting first : 
```
ls -l | awk '{print $8}' | grep ".m4[a,p]$"
```

Once verified, I'll tack on the "| xargs rm" to delete all files listed in the above command : 
```
ls -l | awk '{print $8}' | grep ".m4[a,p]$" | xargs rm
```

---

### Post by psusi on 2008-11-18
```
find . -name '*.m4[ap]' -exec echo {} \;
```

That should print all their names, then hit up and replace echo with rm to delete them.

---

### Post by pgatrick on 2008-11-18
Couldn't you just 'rm *.m4p' and 'rm *.m4a'?

---

### Post by psusi on 2008-11-18
> **pgatrick said:**
> Couldn't you just 'rm *.m4p' and 'rm *.m4a'?

For a single directory, sure... I presume he has an entire directory tree he wants to prune the files from.

---

