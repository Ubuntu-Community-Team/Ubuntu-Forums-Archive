---
title: "system unusable, freeze on start"
date: 2008-12-01
forum: General Help
---

### Post by loserboy on 2008-12-01
I posted once here [http://ubuntuforums.org/showthread.php?p=6288276#post6288276](http://ubuntuforums.org/showthread.php?p=6288276#post6288276) with no answers and normally I wouldn't repost, but I'm out of ideas and can't use ubuntu.

from what I can tell I need someone to tell me how to completely disable my wired nics from trying to load because when I boot, right before it goes to desktop the screen is spammed with a message saying basically "eth1 system error occured". Eventually the desktop startes to load but it never gets there and its a complete freeze.

Ive already commented out eth1 in interfaces to no avail.

eth1 is identified as an onboard LAN card and I disabled it in bios, also no help.

so now I'm stuck...

---

### Post by loserboy on 2008-12-03
after some experimenting, the issue seems to be having multiple lan cards installed. After removing one it looks like my problem is fixed....

---

