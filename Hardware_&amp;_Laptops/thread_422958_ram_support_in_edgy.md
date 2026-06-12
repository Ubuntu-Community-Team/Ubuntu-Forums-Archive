---
title: "ram support in edgy"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by trancepose on 2007-04-25
hi fellaz
i have a question about ram support of ubuntu distros. 
I have 3 Gig ram on my pc and use i386 version of edgy. i have selected this distro in order to prevent from any software in compatibility issues. now my question is, how much of ram is supported in i386 architecture of edgy? i am planning to develop a simple CFD program and using proe

---

### Post by psusi on 2007-04-25
At least that much.  I'm not sure which options were used in the edgy kernel, but worst case is that to support more than 3 gigs you will have to recompile the kernel with the proper options.

---

### Post by Lord Illidan on 2007-04-25
I think you are using the generic kernel, right? Type in uname -r in the terminal. The generic kernel should support 3 gigs fine.

---

