---
title: "[SOLVED] Evolution not starting anymore after system crash"
date: 2008-07-29
forum: General Help
---

### Post by mindhaq on 2008-07-29
Yesterday I had to shutdown my laptop forcefully using the power button (I'll write about this in another thread, had to do with ACPI).

When I now try to open Evolution, it shows the Email screen, with a "loading" message below the accounts. No messages or folders are shown. After some seconds, the window greys out, and that's it.

I tried to start evolution on the shell, with debug enabled and in offline mode - nothing else to report. Nothing gets written into the logfile.

If I try to start it with the --component parameter to start it with anything but "mail", I don't even get a window at all.

How can I repair my Evolution? And why can it even crash so hard?

---

### Post by frup on 2008-07-29
If you don't mind loosing some stuff using synaptic to reinstall it should get it working again.

---

### Post by mindhaq on 2008-07-29
> **frup said:**
> If you don't mind loosing some stuff using synaptic to reinstall it should get it working again.

Well - this would never be an option for me. Evolution keeps business mails for me, and I am obliged by law (!) to keep those.

Luckily, after restarting the computer, Evolution worked again. Very strange, never thought this is something helping me with Ubuntu.

But: this must have been something outside Evolution. gnome-phone-manager didn't start as well when I tried to. Now both are working...

---

