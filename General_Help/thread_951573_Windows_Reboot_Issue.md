---
title: "Windows Reboot Issue"
date: 2008-10-18
forum: General Help
---

### Post by opticyclic on 2008-10-18
My mum had a serious issue with her Windows PC which meant that almost none of the services were starting and she couldn't do anything.
I installed gOS, as it looks nice, as a backup system for her and to be able to look for help online.
I ended up doing a Windows Recovery install to fix her issue, but now there is another problem:

If the PC is switched off XP will not fully boot and will continually restart (or BSOD with Stop 0x0000007B if Automatically Restart is not checked).
However, I can boot into gOS no problem, and when I restart from there XP starts fine.
Also, restarting from XP isn't a problem either.

However, my mum believes that is the fault of Linux and is trying to get me to remove it.

I can't see how it would be an issue unless its something to do with the boot sector which somehow might be preventing all the Windows drivers from starting??

If it was a hardware issue, why would it boot into Linux but not Windows?
I don't understand how a restart works fine but a shutdown/start has problems.

Has anyone else seen/fixed a similar issue?

---

### Post by PocketDog on 2008-10-18
A complete removal of Windows will solve your BSOD issues. Is that an option?

---

### Post by opticyclic on 2008-10-19
Funny. :rolleyes:

Obviously not, since, as mentioned, my mum is trying to get me to remove Linux to fix the issue and she is only (vaguely) interested in having Linux as a backup.

Interestingly, now the XP install disc doesn't recognise that there is already an XP installation.

If I use the disc to 'fix' the MBR can I subsequently get GRUB back on it without reinstalling Linux?

---

### Post by PocketDog on 2008-10-19
Sorry. Yes, you can definitely do that

---

