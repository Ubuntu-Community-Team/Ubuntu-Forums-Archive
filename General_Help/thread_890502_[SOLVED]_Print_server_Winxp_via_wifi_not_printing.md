---
title: "[SOLVED] Print server Winxp via wifi not printing"
date: 2008-08-15
forum: General Help
---

### Post by Alistair George on 2008-08-15
Everything is set up on Linux box, test print shows as sent and can see data going via wifi card, but shared printer on xp box is doing nothing. Having read this fault on other threads does not seem to have a fix for this issue any suggestions pse I am sure its the xp box. But in saying that on Linux printer settings is available 'Windows printer via Samba' does this mean the Samba client is already installed because neither Samba or GSAMbad are installed. Its being found by the Linux Samba service.
Alistair.

SOLVED.
Complex problem associated with Winxp. 
Ensure to uncheck [ ] Enable bidirectional printing
In printer port on xp.
I mentioned spooling was visible. What had apparently happened was due to bidirectional by default a huge backlog was saved in the print spool which was not visible. 
Bring up 'whats in the print que' in XP from printers view and clear all the tests that you have sent to it.
Also suggest you ensure Network printing is checked in Windows add remove programs/Windows.
Cheers,
Alistair.

---

### Post by martynJ on 2008-09-03
Many thanks Alistair ~ that worked for me.

---

### Post by jarobman on 2008-10-08
Same here, this worked for me as well!  Thanks Alistair!

---

