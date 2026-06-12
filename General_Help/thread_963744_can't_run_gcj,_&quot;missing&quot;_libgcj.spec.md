---
title: "can't run gcj, &quot;missing&quot; libgcj.spec"
date: 2008-10-30
forum: General Help
---

### Post by deleopario on 2008-10-30
I need to be able to run gcj as I have some java code I need to use as a library with a program that will take an object file.

I installed gcj, libgcj6-dev, and gdb with aptitude.

When I try to run gcj though, I always get: "gcj: libgcj.spec: No such file or directory"

find / -name libgcj.spec revealed that there is in fact such a file sitting in /usr/lib/gcc/i486-linux-gnu/4.2/. 

Anyone know how to fix this?

---

### Post by deleopario on 2008-10-30
I hate to bump but this hasn't even gotten viewed yet in 40 minutes and I really need to get this working for a project.

---

### Post by gimpmaster3201 on 2009-01-07
Hi

I also have the exact same problem, but unfortunately have not found a solution as of yet. 
Have you made any progress?

Ash

---

### Post by jimbob on 2009-01-07
I had this problem a while back and solved it by completely removing gcj and installing java6 instead.

---

### Post by gimpmaster3201 on 2009-01-08
JimBob

The problem is that I need to use this compiler through no choice of my own.

see:

[http://ubuntuforums.org/showthread.php?p=6512899#post6512899]("http://ubuntuforums.org/showthread.php?p=6512899#post6512899")

---

