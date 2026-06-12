---
title: "How to turn off shutdown splash screen for troubleshooting?"
date: 2008-11-06
forum: General Help
---

### Post by jasper.davidson on 2008-11-06
I'm having some restart/shutdown issues with Ubuntu right now, and I was wondering, how would I turn off the shutdown splash screen so Ubuntu would instead go into text mode and show all the restart/shutdown messages? Also, is there a log somewhere of all the restart/shutdown messages that scroll by? 

Thanks in advance.

---

### Post by Sam on 2008-11-06
On grub, press 'e' to go to edition mode.

Choose the line starting with 'kernel' and press 'e' again.

Remove 'splash' from the line (at the end).

Press 'b' to boot without the splash screen.


You can also remove 'quiet' to get more verbose output.



If you want to turn these settings permanently, please ask.

---

### Post by jasper.davidson on 2008-11-07
Thanks for the reply, Sam, but I don't want to disable the start up splash screen, I want to disable the shutdown splash screen. Is that what your directions are for?

---

### Post by September on 2009-05-21
You may use

```
sudo shutdown -v -h now
```to shutdown and

```
sudo shutdown -v -r now
```to restart without the splash/logo (verbose mode).

It would be lovely to be able to modify the shutdow/reset commands from the top-right menu on the desktop to implement these (through a config file? I dont know).

Edit: To see the verbose text as long as you want, you may omit -h on shutdown.

---

