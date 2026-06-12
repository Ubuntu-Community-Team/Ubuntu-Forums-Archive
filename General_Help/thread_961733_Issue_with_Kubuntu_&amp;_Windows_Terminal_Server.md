---
title: "Issue with Kubuntu &amp; Windows Terminal Server"
date: 2008-10-28
forum: General Help
---

### Post by gulagarchipelago on 2008-10-28
I currently connect to a few different Windows Server 2003 terminal servers using rdesktop & Kubuntu.  The terminal servers are set to allow time redirection, so that whatever the system time is on the local PC, that is the time set on the server.

However, recently when I connect to the servers, my time is always one hour behind, despite the fact that my Kubuntu clock is correct.  When I log into the Windows server, I see that its put me in the "Bogota, Lima, Quito, Rio Branco" time zone (GTB, normaltid).  I need it to place me in the Eastern Time (US & Canada) zone.  What can I do in Kubuntu to correct this?

---

### Post by gulagarchipelago on 2008-10-28
Note that this functions correctly when connecting from a Windows XP machine.

---

### Post by dburnett77 on 2008-10-28
> **gulagarchipelago said:**
> I currently connect to a few different Windows Server 2003 terminal servers using rdesktop & Kubuntu.  The terminal servers are set to allow time redirection, so that whatever the system time is on the local PC, that is the time set on the server.

However, recently when I connect to the servers, my time is always one hour behind, despite the fact that my Kubuntu clock is correct.  When I log into the Windows server, I see that its put me in the "Bogota, Lima, Quito, Rio Branco" time zone (GTB, normaltid).  I need it to place me in the Eastern Time (US & Canada) zone.  What can I do in Kubuntu to correct this?

ntp configuration should have a script for an entry.  Try going to UTC, by updating the clock via the server you want to access.

This business sense is time-critical.  I'd leave out the servers all together if it was me, and just manually set the time.

---

### Post by gulagarchipelago on 2008-10-29
> **dburnett77 said:**
> ntp configuration should have a script for an entry.  Try going to UTC, by updating the clock via the server you want to access.

This business sense is time-critical.  I'd leave out the servers all together if it was me, and just manually set the time.

Well the issue is I have customers connecting from multiple time zones, so I can't just set the time in the normal way.

---

