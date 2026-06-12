---
title: "new cd-rom causes installation problems"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by jmichael on 2007-12-25
I recently switched cd drives from an ide to a sata and got rid of the old ide drive. This has caused problems when I try to update or install apps that need the Ubuntu disc. Every time I put the disc in it launches the auto start but terminal still says there is nothing in cd-rom.

any answers on what i can do to fix this?

---

### Post by PaganHippie on 2007-12-25
Don't know why it's not acknowledging the CD, but you can work around this by commenting out the CD-ROM repos, either in Synaptic, or editing /etc/apt/sources.list by hand.  This will force installs and updates to read everything from the Internet repos.

---

