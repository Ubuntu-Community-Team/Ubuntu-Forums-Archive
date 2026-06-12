---
title: "Accidently deleted libssl3.so.ld!! firefox crashed !!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by vmkid on 2009-05-09
i accidentally deleted the libssl3.so.1d and libsmime.so.ld from my /usr/lib/ dir.
Now when I try to open firefox from command line i get the error : "Couldn't load XPCOM".
i also tried running xpcshell-1..9 which gives the message: "error while loading libraries: libssl3.so.1d". so i copied libssl3.so.1d from another ubuntu deskptop into my /usr/lib dir. but  the copied file is reported to be of unknown type, not a shared library. can anyone help me please? does copying a shared library help or we have to build one, if yes then how?

---

