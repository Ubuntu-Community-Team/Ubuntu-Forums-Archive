---
title: "Want to use all of my RAM"
date: 2011-06-01
forum: Hardware
---

### Post by elliotbeken on 2011-06-01
Hi all i am currently using Ubuntu 11.04 64bit in a VirtualBox setup. i have allocated my ubuntu to use 6gig of ram out of the 8gigs i have in my rig..

i was wondering of there is a script or application i can use to make ubuntu use all of the RAM?

i want to see how the host operating system will cope if the full 6 gigs are in use ?

---

### Post by SeijiSensei on 2011-06-01
Linux will use all the memory you give it.  Whatever isn't used by programs is allocated to disk caching.

If you want a complete inventory of memory usage, run "cat /proc/meminfo" from the command prompt.

---

### Post by Joe of loath on 2011-06-01
Virtualbox allocates all the memory in one go, the host's performance will be no different whatever memory the guest is using.

---

### Post by Sylslay on 2011-06-01
You can use graphic memory as swap. 
Some Idea, but seams to be cool.

If You dedicated half GDDR5 for swap file.

---

### Post by Joe of loath on 2011-06-01
> **Sylslay said:**
> You can use graphic memory as swap. 
Some Idea, but seams to be cool.

If You dedicated half GDDR5 for swap file.

Got a source for this? It doesn't sound terribly plausible.

---

### Post by Sylslay on 2011-06-01
Well , I seen that source on Sabayon/Gentoo froums.

[http://en.gentoo-wiki.com/wiki/Using_Graphics_Card_Memory_as_Swap](http://en.gentoo-wiki.com/wiki/Using_Graphics_Card_Memory_as_Swap)

But is cool idea anyway,
If You figure out how to do it in Ubuntu ,
let me know.

[http://groups.google.com/group/gpu_newbies/msg/62ac37050c5118d3?](http://groups.google.com/group/gpu_newbies/msg/62ac37050c5118d3?)

Never bother to check on destop with GPU-256MB ram, but probably is worth to play with 512 :-)

---

### Post by Joe of loath on 2011-06-01
Wow, it looks possible.

Can't try it though, have integrated graphics XD

---

