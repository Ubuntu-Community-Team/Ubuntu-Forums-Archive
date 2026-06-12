---
title: "undefined symbol error even though it is found"
date: 2008-07-30
forum: General Help
---

### Post by catacuta on 2008-07-30
Hi, When I run a java program I get an undefined symbol error
here it is:
...
lib/libSearch.so: undefined symbol: _ZN5boost6system19get_system_categoryEv


however when I make a grep on the /lib directory, this symbol is found:

grep -r "_ZN5boost6system19get_system_categoryEv" *
Binary file lib/libSearch.so matches

So the symbol is there but somehow it is not recognized, I have no ideas on how to solve this, what about you?

thanks.

---

