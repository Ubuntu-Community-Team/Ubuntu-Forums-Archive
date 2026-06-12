---
title: "VNC says &quot;Wrong Password&quot;"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by JustGus on 2009-09-10
Hi,

In the past I've merrily used RealVNC on my Vista laptop to access my Ubuntu server.  My motherboard subsequently blew out, so I've had to swap my HDD and put it in a new machine. I've since tried to reinstall and get VNC going, but get a message "Wrong Password".  If I disable the password function entirely, under Remote Desktop/Security, I can access it without problem, but for obvious reasons I'd like to secure this.  
Any ideas why it would be giving me this error message - particularly as I've triple checked and am using the same password in the Remote Desktop/Security settings as I'm typing in on my laptop?

Cheers in advance!
G

---

### Post by JustGus on 2009-09-11
In case it helps someone else along the way, I've found a fix for this.  It seems the vncserver app is separate and wasn't communicating with the Remote Desktop.  I went through the password setting instructions via the Terminal, shown here:
[http://www.realvnc.com/support/getting-started.html#4]("http://www.realvnc.com/support/getting-started.html#4")

Gus

---

