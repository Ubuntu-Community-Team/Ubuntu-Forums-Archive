---
title: "problem installing inside a winxp ... which account to log in?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by girogio on 2009-02-12
I've installed xubuntu 8.10 on my desktop from inside winxp.
All ok ... but the instalelr didn't asked me for a password neither an username, so now xubuntu boots regularly but I don't know which account to use! And I can'yt log in (neither I know root accout!)

Is this regular? Should the isntalelr ask me as for a normal ubuntu instalaltion on a new system?

What can I do?

thanks!

Giorgio

---

### Post by lemming465 on 2009-02-14
When it goes to boot, at the grub menu (comes up after you pick the WUBI/ubuntu option from the XP boot menu, if I understood you correctly), boot in *recovery mode*.  You should get a '#' shell prompt running as root.  Try something like *tail /etc/passwd* or *ls /home* to see what user accounts are defined.  Pick one you want to log into and do *passwd ThatLoginName* to reset the password to something you know.  Type *exit* to go finish the multi-user / GUI boot.

If you don't have a "recovery mode" boot item but do have a grub menu, type "e" for edit, arrow down one to the kernel line, "e" again, added **single** to the end, press enter, and press "b" to continue booting.  Carry on as above.

---

### Post by girogio on 2009-02-16
Thankyou! ... solved with your suggestions!
It's the first time for me with Ubuntu .. always used Debian!
Recovery mode was the solution ...

Giorgio

---

