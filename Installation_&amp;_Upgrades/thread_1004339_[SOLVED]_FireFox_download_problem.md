---
title: "[SOLVED] FireFox download problem"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by ingeva on 2008-12-07
After several attempts to solve a problem with Java I tried 8.10 Intrepid which didn't solve the problem and introduced several new ones, so I returned to 8.04 Hardy and most of the 8.10 problems disappeared but a new one has appeared:

FireFox won't download any more. It enters the "save or view" menu, and it can show the contents if I have specified the correct document viewer, but I can't find a way to add application definitions (mimetypes).

I removed the .mozilla directory completely, restarted the system and Java suddenly works (without any updating!) but downloads still don't. I have to use epiphany to do that.

Suggestions?

---

### Post by Pumalite on 2008-12-07
'Complete Removal' in Synaptic for Firefox and then reinstall.

---

### Post by ingeva on 2008-12-07
> **Pumalite said:**
> 'Complete Removal' in Synaptic for Firefox and then reinstall.

Thanks, but I have done that, and I've also reinstalled the whole system from scratch.
None of that helped.

The strangest thing is that it works in epiphany but not in FireFox.

---

### Post by ingeva on 2008-12-08
> **ingeva said:**
> Thanks, but I have done that, and I've also reinstalled the whole system from scratch.
None of that helped.

SOLVED!

I had my home directory backed up to an external disk with NTFS filesystem.
After restoring the file and directory permissions were incorrectly set.

For the "Desktop" directory, where FireFox was supposed to downlod (That's convenient since it doesn't ask if that's the default), there was no access.

Since it still worked for epiphany, and even for IE7 on my Windows computer, I assumed something had happened to my FireFox installation.

An example of jumping too early and too fast (to conclusions).

---

