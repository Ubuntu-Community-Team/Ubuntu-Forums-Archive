---
title: "[SOLVED] CUPS client showing wrong page size"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by teamanx on 2008-03-22
Hello. I have setup a Gutsy CUPS server. I have configured a HP LJ2600n on it, and set the default page size to A4. 
When I try to print from the server itself, it defaults to A4 properly. But when I try to print from a client, it uses Letter as default page size. It happens bot in Linux CUPS clients, and Windows Samba-Cups clients.

Any ideas? Thanks!

---

### Post by teamanx on 2008-03-22
Figured it out. 
- For Linux, I had to edit the file /etc/papersize, and just type on it "A4"
- For Windows, it is a common problem in Samba-CUPS servers. The way to fix it is described here: 
[http://www.linuxprinting.org/kpfeifle/SambaPrintHOWTO/Samba-HOWTO-Collection-3.0-PrintingChapter-11th-draft.html#11_1](http://www.linuxprinting.org/kpfeifle/SambaPrintHOWTO/Samba-HOWTO-Collection-3.0-PrintingChapter-11th-draft.html#11_1)

---

