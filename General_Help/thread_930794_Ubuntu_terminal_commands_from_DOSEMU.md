---
title: "Ubuntu terminal commands from DOSEMU?"
date: 2008-09-26
forum: General Help
---

### Post by WPDOS_user1954 on 2008-09-26
I use an application called xsel that takes whatever is in the Linux "clipboard" (aka "X selection"), and redirects it to a file.  I call it up via Terminal.

My question is this: is it possible to somehow run this xsel application from DOSEMU?  The reason I ask is because I have another DOS application running under DOSEMU that can "shell out" to the DOSEMU command prompt and issue a command, and then resume running.

Were what I'm looking for be do-able, it would then be possible for the application to make use of what had been moved from the clipboard to the file.

Thanks in advance for any help or guidance you can provide.

---

### Post by rossjman1 on 2008-09-26
* The utility unix.com can now execute Linux commands within DOSEMU
  interactively.

Try unix.com /? to find out how to use it.

---

### Post by WPDOS_user1954 on 2008-09-26
Thank you!  I've looked at the unix utility, and it does exactly what I need.

I have a supplementary question, but I'll ask it in a separate thread.

---

