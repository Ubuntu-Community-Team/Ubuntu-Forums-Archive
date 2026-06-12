---
title: "Samba &amp; Openoffice"
date: 2008-10-07
forum: General Help
---

### Post by Koybe on 2008-10-07
Hello,

I have a problem. I'm using a samba server working as a PDC in a mixed (Windows, Ubuntu )client environement.

Everything works fine but a little problem on ubuntu clients :

When I open a document from the samba share directly from openoffice, it asks for credential for 'WORKGROUP' (which is wrong) can't authenticate and directly close the document.

When I open it from Nautilus, evrything works fine.

Any comment, idea on how to resolve that issue.

Thank you

---

### Post by Koybe on 2008-10-09
OK Found it.

You need to join the domaine with the samba client.

---

