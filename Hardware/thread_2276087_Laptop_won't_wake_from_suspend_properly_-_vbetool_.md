---
title: "Laptop won't wake from suspend properly - vbetool 100%cpu"
date: 2015-04-30
forum: Hardware
---

### Post by David_Abergel on 2015-04-30
Hi all,

after some fairly extensive googling, I cannot find an answer to this issue, so hopefully someone here can help.

I'm using an almost-fresh install of xubuntu 14.04.2 on a Dell XPS 13 laptop. When I ask the laptop to suspend (either via the main menu, by closing the lid, or by issuing the pm-suspend command from the terminal), the laptop seems to suspend correctly.

However, when I wake it back up, I initially get a black screen with a flashing cursor in the top-left corner. If I ctrl-alt-f1 to a text terminal, then ctrl-alt-f7 back to the graphical interface, my desktop reappears.

I notice in this case that vbetool is occupying 100% cpu time. If I kill this process (via sudo), the laptop seems to run as normal.

This is, obviously, rather frustrating. So can anyone point me in the right direction for how to fix what appears to be a bug in vbetool? (I tried uninstalling that package, but that made things worse - the laptop would not resume at all.)

Thanks in advance.

David

---

