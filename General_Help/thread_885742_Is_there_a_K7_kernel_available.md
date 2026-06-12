---
title: "Is there a K7 kernel available?"
date: 2008-08-10
forum: General Help
---

### Post by huxterby on 2008-08-10
Before I get to my question, I would just like to bring the Forum Search to your attention. I am accustomed to searching before asking, and have found the forum search here producing a lot of irrelevant threads. (please see screenshot).

Back to my question, I use an AMD Athlon processor which means I need to use the K7 kernel. I opened Synaptic, searched for K7 and found the kernel, linux-headers and restricted-modules. I checked and installed them only to find afterwards (reboot and no K7 on grub menu.lst) that they are dummy upgrade packages.

How do I go about installing the K7 kernel packages?

Thank you in advance.

Huxterby

---

### Post by logos34 on 2008-08-10
The -generic kernel (which is what the 'dummy' pkg refers to I believe) will work just fine.  It will detect your processor type and adjust accordingly

---

### Post by huxterby on 2008-08-10
Thanks logos34. I usually apt-get the Debian kernel from the repo. Good to know that there is still something new to learn every day ;)

Huxterby

---

### Post by logos34 on 2008-08-10
The -generic kernel is pretty darn good,  That said, you could compile your own kernel, which is really easy using an app like [KernelCheck]("http://kcheck.sourceforge.net/").  But even there the most specificity you will get as far as processor family configuration is 'Opteron/Athlon64/Hammer/K8'--obviously not necessarily any improvement since you have a K7 series.

---

### Post by cariboo on 2008-08-10
As far as searching the forum, I agree you do get a lot of false positive. I usually use google with ubuntu as part of the search subject. I always get at least one result for what I'm searching for, and usually a lot more. You don't have to search just the forums for answers to question, as a lot of solutions will work even if they are for other distributions.

Jim

---

