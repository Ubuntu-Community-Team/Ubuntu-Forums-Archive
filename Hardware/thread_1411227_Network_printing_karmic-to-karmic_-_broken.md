---
title: "Network printing karmic-to-karmic - broken?"
date: 2010-02-19
forum: Hardware
---

### Post by Steve Roscio on 2010-02-19
Hi -

Two newly installed karmic systems, one setup as a print server, the other as a print client.  However, I cannot see any of the server's printers from the client.
Locally printing from the server works OK.  Both on the same LAN, I can telnet to 631 from client to server (to test that the port is open), no firewalls are in the way.  Both are 64bit if it matters.

On server, I have System => Administration => Printing => Server => Settings... "Publish shared printers" checked.  The printer policies are "Shared" checked, access control open for all.

On the client, I have "Show printers shared by other systems" checked.  But none show up.

Did this break in karmic?  Suggestions on how to fix?

Thanx in advance,
- Steve

---

### Post by Steve Roscio on 2010-03-10
Found cause - not only do they need to be on the same LAN, but in the same subnet too.
Working now.

---

