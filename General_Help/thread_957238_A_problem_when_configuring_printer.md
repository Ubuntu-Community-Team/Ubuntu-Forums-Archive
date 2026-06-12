---
title: "A problem when configuring printer"
date: 2008-10-24
forum: General Help
---

### Post by jingqi on 2008-10-24
I want to fix a remote hp printer through Samba client. I do the followings, entering "System", clicking "Administration", clicking "Printing", and then get no response from the Ubuntu. How can I make it right? Thanks in advance.

---

### Post by plucky on 2008-10-24
> **jingqi said:**
> I want to fix a remote hp printer through Samba client. I do the followings, entering "System", clicking "Administration", clicking "Printing", and then get no response from the Ubuntu. How can I make it right? Thanks in advance.

**System > Administration > Printing > Server Settings** and tick the box that says "Show printers shared by other systems".

If that doesn't work,please give more information about your setup,network,systems etc.


Good Luck

---

### Post by jingqi on 2008-10-24
> **plucky said:**
> **System > Administration > Printing > Server Settings** and tick the box that says "Show printers shared by other systems".

If that doesn't work,please give more information about your setup,network,systems etc.


Good Luck

Thanks anyway. But it's not responding at all when I click "Printing", that is I can not get access to "Server Settings".

---

### Post by plucky on 2008-10-24
> **jingqi said:**
> Thanks anyway. But it's not responding at all when I click "Printing", that is I can not get access to "Server Settings".

Open a terminal and type ```
system-config-printer
``` and see if there are any error messages when the printing GUI opens.

If that doesn't work, then start Firefox and in the address bar copy and paste ```
http://localhost:631/admin/
``` to access the CUPS interface.Try and set up the printer server from there.


Good Luck

---

