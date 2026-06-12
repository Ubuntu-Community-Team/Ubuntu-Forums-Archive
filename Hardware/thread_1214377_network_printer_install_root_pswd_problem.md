---
title: "network printer install root pswd problem"
date: 2009-07-15
forum: Hardware
---

### Post by Tholley on 2009-07-15
This computer is connected to a network printer via wireless network, connected to a router at the main computer. the last time i printed anything was 2 weeks ago and all worked fine.

today it says my printer may not be connected, but it is, and will print from the other computer. So I figured I would try and let it _find_ the printer again which it did, found the drivers, but at the last step, it asks for "Password for root on localhost?". It shows the user name is root and when I type in my normal password for everything else, it says "Not Authorized - the password may be incorrect".

I have tried every imaginable password I have ever used, and even changed the user name to this computer and the other computer, but all the same.

what am I not doing right here?

Help...

---

### Post by rimu_miro on 2010-07-06
try running  'system-config-printer' as root if you are experiencing permissions  problems (sudo system-config-printer)

---

