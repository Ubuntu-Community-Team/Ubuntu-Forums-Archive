---
title: "Problem with Synergy - unable to connect"
date: 2008-07-19
forum: General Help
---

### Post by jthestness on 2008-07-19
I have been using synergy between a Windows XP laptop and a Linux PC (7.10 Gutsy Gibbon) for a couple months.  The Linux box was the server and the PC was the client.
Seemingly randomly, synergy quit working a couple days ago.  When trying to connect the client on the PC, I get the error message:

INFO: Synergy client 1.3.1 on Microsoft Windows Server XP
NOTE: started client
ERROR: failed to connect to server: Timed out
NOTE: stopped client

I tried using the Linux box as the client and the PC as the server, and everything works fine.  I have reinstalled synergy on both machines.  Further, from either machine, I can ping the other with no problems.
Has anyone encountered such problems?

---

### Post by jthestness on 2008-07-21
Fixed: It turned out that the firewall gui, Firestarter, was not starting properly and was aparently causing communication to be dropped from synergy clients.  I must have installed an update to Firestarter a few days ago.  I removed Firestarter and everything works fine again.

---

