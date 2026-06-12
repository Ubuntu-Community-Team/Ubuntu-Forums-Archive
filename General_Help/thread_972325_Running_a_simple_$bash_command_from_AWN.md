---
title: "Running a simple $bash command from AWN"
date: 2008-11-05
forum: General Help
---

### Post by sstecken on 2008-11-05
When I bash: 

~/Applications/vuze/vuze

Eveything runs fine.

When I attempt the same command from AWN, it doesn't work.

Any idea on how to fix this?

---

### Post by Coreigh on 2008-11-05
It sounds like a permissions issue. If AWN is running as an unprivileged users then you would need to some how sudo the command.

Then again if the command itself does not require sudo then I don't know and we're back to square one.

---

