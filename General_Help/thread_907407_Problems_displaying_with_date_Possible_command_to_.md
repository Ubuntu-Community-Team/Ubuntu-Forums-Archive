---
title: "Problems displaying with date: Possible command to fix?"
date: 2008-09-01
forum: General Help
---

### Post by sstecken on 2008-09-01
I'm having trouble displaying my files via the date created.  How can I batch reset the date created, modified, accessed parameter for a group of files?  Is there a specific command to do this?

---

### Post by pytheas22 on 2008-09-01
You can use the command 'touch' to change access times, among other things.  Take a look at its [man page]("http://www.manpagez.com/man/1/touch/") for the details.  I'm not sure if you can change actual creation time--keep in mind that the system will probably try to prevent you from doing that, because it can be used to exploit security vulnerabilities--but you can at least change modification and access times.

---

