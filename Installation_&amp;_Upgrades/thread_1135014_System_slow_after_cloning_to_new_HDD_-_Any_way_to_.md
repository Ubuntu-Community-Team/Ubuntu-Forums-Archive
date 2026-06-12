---
title: "System slow after cloning to new HDD - Any way to repair"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by super_czar on 2009-04-24
I have a Ubuntu (7.10)system running as a server 

The primary HDD on the system started developing bad sectors so I cloned the old HDD to a new one

Now when the system had started developing bad sectors, it started exhibiting some weird behavior (slow startups - specifically the taskbar unresponsive for a long time after startup, apache and samba server starting after a long time etc)

Now the cloned system has the same symptoms
I am guessing this is because the data from the bad sectors which got skipped during copy contains some startup script or binary that the system tries to load at startup and keeps looking for the data (which does not exist)

Is there a way I can repair the existing install?

---

