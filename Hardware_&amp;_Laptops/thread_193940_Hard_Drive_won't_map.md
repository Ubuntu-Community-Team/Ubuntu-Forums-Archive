---
title: "Hard Drive won't map"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by LsrLine on 2006-06-10
I've been trying a lot of things to get my system up and running and I've had no success because I need to recover everything on my hd.  So this is what I wanted to do.  Boot off the Ubuntu CD and back up everything that way.  It detect my hard drive, but says it need to be mounted, but when i right click and click mount it say Permissions denied.  How can I mount this hard drive, so I can copy everything to my other hard drive?

EDIT: I meant to say mount in the title

---

### Post by gborzi on 2006-06-10
Have you tried, from a shell
> sudo mount /dev/hdax
where x is the partition number ?

---

