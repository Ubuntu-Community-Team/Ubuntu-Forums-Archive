---
title: "SSD and Ubuntu"
date: 2011-02-07
forum: Hardware
---

### Post by jonsku on 2011-02-07
Howdy!

I was just wondering what is the state of SSD support on Ubuntu? Sure, I can use them but, there's still a couple of things that might have rough edges:

- The sheer TRIM command is supported by the kernel, but it's kind of hard to tell whether it is actually dispatched through the whole OS. Is it actually integrated to the filesystem (and possibly some other pieces)?

- Is partition alignment performed by the installer? For now I've been using manually "cfdisk -s 56".

---

