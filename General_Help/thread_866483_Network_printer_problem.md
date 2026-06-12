---
title: "Network printer problem"
date: 2008-07-21
forum: General Help
---

### Post by luceerose on 2008-07-21
My network printer won't print CERTAIN things. Let me clarify;
Test page - YES
Print from Openoffice - YES
Print from Firefox - NO
Print from Document Viewer - NO

Here is my setup, (I'm trying to print from the 2nd computer);
Wired network with router
Routers IP: 192.168.1.254

1st computer;
Computer Name: GUITAR-NET-1
Static IP: 192.168.1.105
Subnet: 255.255.255.0
Attached Printer: usb://CanonMP780 (gutenprint driver) (Policies:Shared)

2nd computer
Computer Name: larsenguitars-counter
IP: Roaming
Subnet: -
Network Printer: ipp://GUITAR-NET-1.local:631/printers/MP780

Both computers running a fairly recent install of Hardy,
No Samba installed

All printing works from the 1st computer, just not the 2nd.
Anyone experienced anything like this ?
Have I set up something wrong ?
Should I try a static IP on the 2nd computer ?

---

