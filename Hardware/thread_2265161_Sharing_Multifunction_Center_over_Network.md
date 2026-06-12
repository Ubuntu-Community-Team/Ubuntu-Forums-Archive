---
title: "Sharing Multifunction Center over Network?"
date: 2015-02-13
forum: Hardware
---

### Post by CybaCowboy on 2015-02-13
I have a Brother MFC-J6920DW and courtesy of the official (Brother) software and drivers, I have both printing and scanning working fine over the wireless network (Wi-FI) - that is, Simple Scan, XSane and all third-party programs supporting printing and/or scanning can scan from or print to the MFC-J6920DW using wireless networking (Wi-FI), with no physical connection to my computer...


But when I try to scan using Qoppa Software's PDF Studio: Pro, it asks for the "scanner host" - if I leave this as the default ("localhost"), it tells me:
*Unable to connect to sanned at localhost/nConnection refused.*


Any help in getting this corrected would be appreciated.

---

### Post by ajgreeny on 2015-02-13
That's probably because it is not connected to localhost; it is remote as far as the software is concerned.

You will probably need the local IP address of the printer, eg 192.168.#.# or similar. The last two digits could be found probably from your printer setup on an already connected machine to that printer or from the router web admin pages.

---

### Post by CybaCowboy on 2015-02-13
I know the IP address of my multi-function center, it's listed in my modem/router configuration pages and it's the same IP address I used when configuring the official drivers/software via Terminal...

But if I enter the IP address as the "SANE host" in PDF Studio: Pro, it tells me (via three different pop-up boxes):
** Unable to connect to sanned at #.#.#.#/nConnection refused.*
** There are no SANE sources installed.*
** <nothing, empty dialog box>*

---

### Post by ajgreeny on 2015-02-14
I have no knowledge or experience of Qoppa Software's PDF Studio: Pro, so I can not help you more with this, I'm afraid.

---

### Post by gifford on 2015-02-14
Since your printer and scanner work outside of software you are having trouble with, I would post your question with Qoppa.
Your Ubuntu system is working...the issue is with the individual third party software.

---

### Post by jajodo on 2015-02-28
Same problem.  Here is the solution on the qoppa site.
Basically saned service must be running.
Best.

[http://kbpdfstudio.qoppa.com/?p=185](http://kbpdfstudio.qoppa.com/?p=185)

---

