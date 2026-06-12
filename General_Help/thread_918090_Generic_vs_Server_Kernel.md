---
title: "Generic vs Server Kernel"
date: 2008-09-12
forum: General Help
---

### Post by chefweb on 2008-09-12
Hi,

can me somebody explain what's the difference between the generic and the server kernel?
All what I know is that the server kernels supports PAE and generic not. Is it wise to run the server kernel on a latop?

---

### Post by wolfen69 on 2008-09-12
> **chefweb said:**
>  Is it wise to run the server kernel on a latop?

i would not do that. if you want a minimal install, you can get Ubuntu Minimal [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). even then, it will take some work to get everything on the laptop working.

---

### Post by chefweb on 2008-09-12
what is the difference to generic??

---

### Post by bodhi.zazen on 2008-09-12
[http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)

[http://www.serverwatch.com/tutorials/article.php/3716396](http://www.serverwatch.com/tutorials/article.php/3716396)

---

### Post by Vivaldi Gloria on 2008-09-12
Here is a list of the server-specific kernel optimisations that we include:

    *      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

    *      Pre-emption is turned off in the Server Edition.

    *      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

    *      The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.

    *      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.

    *      Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.

    *      For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.

    *      When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.


from

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

