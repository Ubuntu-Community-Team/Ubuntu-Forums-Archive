---
title: "Makeinfo Missing or too Old"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by newport_j on 2009-08-27
I am trying to install an older version of gcc (3.3.5) for two applications that will not work with the current version of gcc (4.2).

I ran the ./configure command and everything went okay except I got this warning.

checking for makeinfo... no
configure: warning: 
*** Makeinfo is missing or too old.
*** Info documentation will not be built.
checking for recent Pod::Man... yes
checking for flex... (cached) /bin/sh ./../missing flex
checking for bison... (cached) /bin/sh ./../missing bison


Now is this warning about makeinfo being missing or too old something that should concern me? If it is something to be concerned about then how do I fix it?

Also are the last two lines of missing flex and missing bison something that I should be concerned about?

Some recent post said the missing Makeinfo file missing is corrected by:

sudo apt-get install texinfo 

Is that correct - will that work?

Any help appreciated.

Newport_j

---

