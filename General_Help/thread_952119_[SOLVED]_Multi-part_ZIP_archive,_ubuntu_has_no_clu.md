---
title: "[SOLVED] Multi-part ZIP archive, ubuntu has no clue what to do...."
date: 2008-10-18
forum: General Help
---

### Post by Monotoko on 2008-10-18
Hiya, i have a multi-part ZIP archive
hello.zip and
hello.z01

when i try to extract the ZIP, i get: 
```

warning [/home/monotoko/Desktop/NT51%2BWP2_CTFORUM(2).zip]:  zipfile claims to be last disk of a multi-part archive;
  attempting to process anyway, assuming all parts have been concatenated
  together in order.  Expect "errors" and warnings...true multi-part support
  doesn't exist yet (coming soon).
file #1:  bad zipfile offset (local header sig):  4

```

Is there anything that can handle multi-part archives in ubuntu?

---

### Post by Pro-reason on 2008-10-18
I believe that this is how you do it, although I've never needed to:

```

cat hello.z01 hello.zip > hello-concatenated.zip
zip -F hello-concatenated.zip
unzip hello-concatenated.zip

```

---

### Post by Monotoko on 2008-10-18
Thank ye, that worked :)

---

### Post by shreepads on 2009-10-07
Thanks!!

Just a note for anyone with more files, the correct sequence to concatenate is

.z01
.z02
.z03
...
.zip

---

### Post by ashmew2 on 2011-04-17
Thanks loads.
I had Seven Files in total :

XX.z01
XX.z02
XX.z03
XX.z04
XX.z05
XX.z06
XX.zip

All i did was :
```

cat XX.z01 XX.z02 XX.z03 XX.z04 XX.z05 XX.z06 XX.zip > Complete.zip
unzip Complete.zip

```

the -F switch didnt seem to work..My extracted file runs fine although it complained about some stuff at the time of extraction. Thanks ! :)

---

