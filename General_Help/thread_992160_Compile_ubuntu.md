---
title: "Compile ubuntu"
date: 2008-11-24
forum: General Help
---

### Post by Woody1987 on 2008-11-24
I noticed that ubuntu is compiled as i386 which means it doesnt take advantage of some of the new features in newer CPUs. I would like to be able to compile ubuntu myself as i686 or at the very least compile all programs that i install on it from source much like gentoo. Is this possible, if so how?

---

### Post by dexter on 2008-11-24
What kernel are you running? Could you post the output of 'uname -a'. 

I'm using a 64bit system now so I can't check but i was quite sure that Ubuntu uses i686 or generic kernels on 32bit platforms, no longer specific i386 kernels. The generic kernel checks at run time what cpu you have and enables its' enhancements.

---

### Post by Woody1987 on 2008-11-24
im currently on a 64bit system, but i want to install it on my 32bit laptop. I am currently in the process of trying to install gentoo which is proving to be a pain in the ***. I didnt realise that was the case with the generic kernel, i remember when i did use 32bit the kernel did say generic so im assuming it will be the case when i give up on gentoo and move it back to ubuntu. I would still like to be able to compile all the programs myself though.

---

