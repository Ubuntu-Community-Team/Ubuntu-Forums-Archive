---
title: "after Jaunty update: Can't open terminal window"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by mindless1973 on 2009-05-04
Hi,

After I upgraded from Intrepid to Jaunty, I can't open a terminal window any more. I just get the following error message:

There was an error creating the child process for this terminal

I also cannot start xterm directly or via the Launcher.

any help appreciated!

Thanks,
bye
Marcus.

---

### Post by arnold.pietersen on 2009-05-06
I get the same message.

Any help will be appreciated

---

### Post by mindless1973 on 2009-05-21
The problem still persists. It seems to be a problem with PTY in general. I also cannot do any package updates via the update manager, I get a messagebox telling me:

> 
Error failed to fork pty


There is obviously a problem with the virtual PTYs that also why I cannot open a terminal window. However, switching to a text terminal by pressing CTRL-ALT-F1 does work.

Unfortunately I don't know how to troubleshoot further on as I don't know much about the Linux internal use and behavior of virtual PTYs. 

So, if someone could support me here, this would highly be appreciated!

bye
Marcus.

---

