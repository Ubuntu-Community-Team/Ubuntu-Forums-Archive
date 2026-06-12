---
title: "probs with dependency installing spideroak"
date: 2008-07-21
forum: General Help
---

### Post by mvanstone88 on 2008-07-21
Has anyone had any experience/problems with installing spideroak ?

I'm getting "Dependency unsatisfiable. Libncurses5.

---

### Post by Taxman415a on 2008-07-21
What version of Ubuntu are you running? And is it i386 or 64 bit or what? I'm running 32bit 8.04 and I have libncurses5 installed. Are you trying to install on a different version of Ubuntu?

---

### Post by commonplace on 2008-08-27
Resurrecting this thread because I'm having the same problem now on a laptop with a clean install of Ubuntu 7.10. Same problem as the OP described, it says "Error: Dependency is unsatisfiable: libncurses5"

I've verified that libncurses5 is installed (it was, by default). Any idea what could be wrong? This is the first time I've had a problem installing SpiderOak before.

/Kevin

---

### Post by commonplace on 2008-09-10
It turned out to be something very simple, which is that I was installing the version of SpiderOak made for Hardy (8.04) and the box I was trying to install it on was still running Gutsy (7.10). SpiderOak's support sent me the link to the installer for Gutsy and then it worked just fine.

/Kevin

---

