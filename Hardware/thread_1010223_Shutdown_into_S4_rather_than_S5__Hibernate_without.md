---
title: "Shutdown into S4 rather than S5? / Hibernate without saving state"
date: 2008-12-13
forum: Hardware
---

### Post by smiler_jerg on 2008-12-13
I'm trying to get Wake on LAN (WOL) to work for my headless box (HP something-or-other running Ubuntu Server 8.04). The issue is, the BIOS only supports WOL in S4 (hibernate) state.

For a desktop PC, this might not be so bad, but it's not great in a server-like context. When a service is stopped, it should stop, not be suspended. This can be a problem with SSH (which doesn't close open connections), BitTorrent (which doesn't announce it's leaving to the tracker), Samaba, Avahi, etc.

So what I need is one of the following:
a) A way to stop services before hibernating. Is there a script for this?
OR
b) A way to hibernate without 'hibernating'. i.e. running 'pm-hibernate' will actually shutdown, but tell the BIOS it's in S4.
OR
v) A way to shutdown but telling the BIOS to enter S4 rather than S5.

As far as I can tell, the only different between S4 and S5 is what happens when switched back on, and what the BIOS thinks is happening.

Any ideas?

---

