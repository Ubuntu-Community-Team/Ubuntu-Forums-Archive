---
title: "Samba printer share - nearly working..."
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by usugar on 2006-10-20
Is this the place for printer queries?  Not really sure whether this is printer or a network problem but here goes...

I have an HP PSC1215 printer attached to my main Windows box.  My Ubunutu machine shares files with this and other computers in the house via a wireless LAN.  This seems to work fine, although I have noticed that while the windows machine accesses the Linux shares instantly, the Linux machine takes quite a long time to read the drives on the windows machine - not sure whether this is relevant.

I have tried to set up the printer using the System-Administration-Printing.  The printer type is set as "Network Printer - Windows Printer (SMB)" and the hostname and printer name are correct.

As the PSC1215 doesn't appear in the list of installable printers, I have chosen the PSC1200.  The windows driver (i.e. the driver installed on the windows machine for local printing) is also for the PSC1200 and works fine so I figure this should work too.

When I try to print, here's what happens:

- on the Linux machine, the job appears in the job queue.  After a while it disappears again and the printer status returns to Ready.

- on the Windows machine, the job appears in the print queue.  64kb spools out.  The printer makes a few half hearted-noises, but doesn't get as far as pulling a sheet of paper through.  Then nothing - and in fact I can't even cancel the job from the Windows print queue and have to re-boot the machine if I want to print anything else.

Anyone have any experience of this sort of problem?

cheers

---

### Post by patrice on 2006-10-28
> **usugar said:**
> Is this the place for printer queries?  Not really sure whether this is printer or a network problem but here goes...

I have an HP PSC1215 printer attached to my main Windows box.  My Ubunutu machine shares files with this and other computers in the house via a wireless LAN.  This seems to work fine, although I have noticed that while the windows machine accesses the Linux shares instantly, the Linux machine takes quite a long time to read the drives on the windows machine - not sure whether this is relevant.

I have tried to set up the printer using the System-Administration-Printing.  The printer type is set as "Network Printer - Windows Printer (SMB)" and the hostname and printer name are correct.

As the PSC1215 doesn't appear in the list of installable printers, I have chosen the PSC1200.  The windows driver (i.e. the driver installed on the windows machine for local printing) is also for the PSC1200 and works fine so I figure this should work too.

When I try to print, here's what happens:

- on the Linux machine, the job appears in the job queue.  After a while it disappears again and the printer status returns to Ready.

- on the Windows machine, the job appears in the print queue.  64kb spools out.  The printer makes a few half hearted-noises, but doesn't get as far as pulling a sheet of paper through.  Then nothing - and in fact I can't even cancel the job from the Windows print queue and have to re-boot the machine if I want to print anything else.

Anyone have any experience of this sort of problem?

cheers

I have exactly the same problem with an HP PSC1210 which does appear in the list of installable printers. I havn't figured out yet what to problem is.

---

### Post by patrice on 2007-05-13
Found the problem! Bidirectionnal mode must be disabled in the windows printer's configuration,

---

### Post by tgalati4 on 2007-05-13
Thanks for sharing.

Welcome to the forums.

---

