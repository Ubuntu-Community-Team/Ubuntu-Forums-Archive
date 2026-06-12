---
title: "Thinkpad X31: wake from hibernate fails in Edgy"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by matthewn on 2006-12-19
Greetings. I have a Thinkpad X31 that suspended and hibernated problem-free with Dapper. But with Edgy, though suspend works fine, hibernate is a real trouble.

About 90 percent of the time (not always!), on waking from hibernate, I first get the usual usplash screen, but then when the display should be switching over to X and asking me for my password, everything goes blank.

Trying to switch to a different virtual console has no effect; the only thing I can do is press Ctrl-Alt-Delete and listen to the machine shut down and reboot, at which point the display comes back to life. Any ideas how I go about troubleshooting this very annoying behavior?

---

### Post by matthewn on 2007-01-11
I'll answer my own question in the hopes it might help someone else. Sadly, the solution to this problem was to re-install Edgy. I had done an upgrade from Dapper to Edgy. Reinstalling Edgy (formatting the root partition in the process) solved everything.

---

