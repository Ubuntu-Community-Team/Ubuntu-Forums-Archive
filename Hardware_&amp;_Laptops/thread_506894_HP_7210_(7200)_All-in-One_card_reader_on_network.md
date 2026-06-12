---
title: "HP 7210 (7200) All-in-One card reader on network"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by cyb3rj on 2007-07-22
I recently got the scanning to work across the network, so now I am optimistic that there has to be a way for the card reader to work across the network.

Does anyone have this working?

Does anyone know of an initiative to get this working?

To be clear, this printer is accessible via network and is not attached to anything by USB; my goal is to keep it that way.  So far, my recourse has been to access the card reader via smb through a windows machine (clearly undesirable for a long-term solution).

---

### Post by cyb3rj on 2007-07-22
Well I feel numb (especially answering myself).  The HP tools that are easily available from the repositories have the ability to get images from the card reader!  I'm not sure about which package this is is (maybe simply hplip?).

HPLIP Toolbox - Printer Toolbox
$ hp-toolbox
^^ if one really likes running things from a console

---

