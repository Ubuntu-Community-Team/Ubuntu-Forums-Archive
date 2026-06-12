---
title: "Hard Link vs. Soft Link"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Anubis69 on 2009-03-21
Please can anyone tell me what's the advantages of hard links, 
what's the advantages of soft links, and wehn I would use one over the other? 

Thanks

---

### Post by tommcd on 2009-03-21
For the simple (practical) answer, see:
[http://www.linuxquestions.org/questions/solaris-opensolaris-20/difference-between-soft-link-and-hard-link-424007/](http://www.linuxquestions.org/questions/solaris-opensolaris-20/difference-between-soft-link-and-hard-link-424007/)
[http://www.linuxforums.org/forum/misc/5870-hard-soft-links.html](http://www.linuxforums.org/forum/misc/5870-hard-soft-links.html)
For the more complex (technical) answer, see:
[http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html](http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html)
[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)
So a soft link is like a short cut; and a hard link is more like a mirror copy of the file. In practice I always use soft links. I have very rarely, if ever, seen a tutorial on something that recommended hard linking. Use soft links unless you have an explicit reason for needing a hard link.

And welcome to the Ubuntu forums!

---

