---
title: "Problems installing bkupexec agent for Linux"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by sinister1 on 2009-05-13
Hello,

I am having some difficulties installing the Linux bkupexec agent.

Everything seems to go alright but when i want to start the agent.be it comes with:

-bash: ./agent.be: No such file or directory

i think there is al file which is called when starting the agent but i cant see which file.

Google doesn't help (my error message to generic i guess)
I've searched the ubuntu forums without any result.

Can someone help me?

SPECS Server:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.2
Release:    8.04
Codename:    hardy

Thanks

---

### Post by sinister1 on 2009-05-13
You need to install the "ia32-libs" package if you are using a 64bit OS.

After this the agent will start!


Case Closed!!

---

