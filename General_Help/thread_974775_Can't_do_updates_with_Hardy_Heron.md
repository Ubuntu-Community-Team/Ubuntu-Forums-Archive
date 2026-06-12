---
title: "Can't do updates with Hardy Heron"
date: 2008-11-07
forum: General Help
---

### Post by Sitting Duck on 2008-11-07
Hello,

I just upgraded from Feisty Fawn to Hardy Heron.  When I try to use a packet manager, I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Could this be related to Moblock?  I just installed it as well...

Thanks in advance for any tips.

---

### Post by Stenrad on 2008-11-07
Hi there!

To cure that just open up a terminal and type:-

> sudo dpkg --configure -a

Should sort things out for you. :-)

All the best,

Stenrad.

---

### Post by Sitting Duck on 2008-11-07
Thank you for your reply Stenrad,

I already tried your suggestion but it leads to a warning screen about Moblock...

I'll search these forums to find a way to uninstall Moblock to see if it solves my problems,

---

### Post by jre on 2008-11-08
During installation of moblock-control you will be shown some warnings and are prompted some questions. Read (and answer them) and then **continue**.
So this means you will have to click e.g. on "OK". (Or toggle there by pressing "TAB" and then hit "RETURN".)

---

