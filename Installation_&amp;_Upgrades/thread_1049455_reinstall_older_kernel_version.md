---
title: "reinstall older kernel version"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Dan_Dranath999 on 2009-01-24
Recently i had to do an clean hardy install: it installed with 2.6.24-19 kernel, and just afterwards, it downloaded 2.6.24-23 and been using that one by default.  Anyway, it seems that the older kernel got screwed up somehow (won't configure X properly) so i removed it through synaptic. No big deal, i wasn't using it.

But now i need an older kernel version, so i can test if a particular problem has to do with my current kernel:  **Zsnes and sdlmame freeze when trying to close them, zsnes doesn't have sound despite the recommended settings, and sdlmame won't even load any game** (i have 3 versions of sdlmame: the 0.123 from the repositories, 0.128u7 and 0.129u2 from the developer's home page. NONE SEEMS TO WORK!)

 **--BUT THEY ALL WORKED BEFORE THE CLEAN-INSTALL** (i was using Hardy, and screwed up the system trying to make my mic work)

**So i suppose i was using kernel 2.6.24-21 or 22**, ¿what packages do i have to install to have another kernel available?

Thank you people...

---

### Post by Dan_Dranath999 on 2009-01-25
-----------------------------------?

---

### Post by Dan_Dranath999 on 2009-01-26
figured out myself, thank you, community...

-linux-image-xxxx
-linux-restricted-modules-xxxx
-linux-ubuntu-modules-xxxx

---

