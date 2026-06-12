---
title: "[BUG] virtual terminal and kernel panic"
date: 2008-11-13
forum: General Help
---

### Post by frank_n on 2008-11-13
Ubuntu 8.10, 32-bits.

First, switch to a text console, e.g. console_4,
with <ctrl><alt><f4>. Login as root.

Then use loadkeys and assign SAK to some key,
e.g. <ctrl><alt><break>.

Finally, press SAK. Result:
-  attempt to kill init
-  kernel panic

Can somebody try this on his own hardware?

Thanks a lot.

Frank

---

### Post by frank_n on 2008-11-14
I tried sundry assignments of SAK in the text console,
e.g. even innocuous one like F12. They all lead to 
kernel panic.

It does not seem it is a problem with my hardware since
on the same hardware openSuSe 11 does permit SAK in pure
text mode, that is no X running. 

However, even openSuSe goes belly up is SAK is pressed
in Console_7, X graphics.

---

