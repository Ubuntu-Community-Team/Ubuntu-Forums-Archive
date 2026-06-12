---
title: "[SOLVED] How to delete file named &amp;quot;(null)&amp;quot;"
date: 2008-08-29
forum: General Help
---

### Post by osx on 2008-08-29
Not sure how it happened, but I have somehow ended up with a file that Ubuntu says is named "(null)" (without the quotes). For several months I have been using Fugu to remotely access and edit files on the system, but his morning I came in and a filed named (null) has appeared and I am unable to delete it. The size of the file is the same as a file I had been working on, but I can't even cat the contents. No matter what command I attempt to perform on it, I get a message:

 -bash: syntax error near unexpected token `null'

I don't need the contents of the file as I already have it saved in another location, but how do I get rid of this one named (null)?:confused:

---

### Post by sisco311 on 2008-08-29
try:
```
rm "/path/to/file/(null)"
```
or
```
cd /path/to/file/
rm "(null)"
```

---

### Post by maybeway36 on 2008-08-29
Try this:
```
rm \(null\)
```

---

### Post by osx on 2008-08-29
> **sisco311 said:**
> try:
```
rm "/path/to/file/(null)"
```
or
```
cd /path/to/file/
rm "(null)"
```

I didn't try your second suggestion, but the first:

rm "path/to/file/(null)"

worked perfectly.

Thank you very much.

---

### Post by sisco311 on 2008-08-29
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by ilrudie on 2008-08-29
I realize the thread has been solved but this is related and has more general uses than just null.  

```
ls -li        #to find out the inode number
find -indode <inodenum> -exec rm {} \;
```This should allow you to delete pretty much anything.  Null, things with unprintable characters... its handy in a pinch.

---

