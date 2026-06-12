---
title: "How to delay boot for hard drive spin-up?"
date: 2015-06-28
forum: Hardware
---

### Post by kenneyjs on 2015-06-28
I've been searching for an answer for this for a while.  I need to add a 2 or so minute delay during boot so that ubuntu will have discovered all of the drives (36 drives in jbod connected via LSI HBAs to external enclosures) before mounting drives.  All of the threads that I can find, talk about speeding up boot, I would like to slow it down so that the drives can be discovered before they are attempted to be mounted.

Any ideas/suggestions?

Thanks!

---

### Post by weatherman2 on 2015-06-28
My suggestion is to take the partitions that are slow to mount out of your /etc/fstab file and don't mount them there.  Instead, mount them after login with a script.  You can put the mounting commands in the file /etc/rc.local .  I have done this myself.

---

