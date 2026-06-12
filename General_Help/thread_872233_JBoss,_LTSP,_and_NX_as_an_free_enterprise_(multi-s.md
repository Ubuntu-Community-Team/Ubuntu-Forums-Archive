---
title: "JBoss, LTSP, and NX as an free enterprise (multi-site) terminal/application server"
date: 2008-07-27
forum: General Help
---

### Post by olivesandtrees on 2008-07-27
This might be a bit of a broad post but here goes...

At this time our Java/JBoss based application is not optimized for WAN communication.  It can use up to 5Mb-10Mb of bandwidth to load certain sections of the application, mainly because of the way our developers implemented Java Message Service (JMS).

My company wishes to deploy Ubuntu based terminal/JBoss application servers for multi-site environments to increase remote user performance without the high cost of deploying a Window Terminal Service server.

We would like to enable the clients to boot into their regular OS (Windows XP/Vista or Mac OS X) and then establish a terminal session with the Ubuntu LTSP server.  Which after testing seems very possible with NX and LTSP.

The problem I am running into is that even after integrating NX with LTSP on the server, NX connections are still limited to 2 connections because I implemented NX Free Edition.  My thinking was that by implementing NX with LTSP it would get around this issue.

Any thoughts or suggestions about implementing a low-cost LTSP solution for this type of remote environment would be greatly appreciated.

---

### Post by terry f on 2008-07-27
this probaly does not help but I think [Edubuntu]("http://en.wikipedia.org/wiki/Edubuntu") implements LTSP thin client.

---

### Post by olivesandtrees on 2008-07-27
Thanks for the post, but implementing LTSP or NX is not the problem.  It's connecting **remote clients** to the LTSP server through a site-to-site VPN tunnel when they have already booted into a proprietary OS.

---

### Post by terry f on 2008-07-28
Are you using nx to act as a way to remote desktop or what?

I also found this, still don't know if it helps. [http://www.ltsp.org/twiki/bin/view/Ltsp/FreeNX]("http://www.ltsp.org/twiki/bin/view/Ltsp/FreeNX")

Instead of NX you could use VNC but lose the advantage of NX.

---

