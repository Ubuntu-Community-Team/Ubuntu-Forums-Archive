---
title: "Install UNR on Ubuntu 7.10 Gutsy?"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by mitchbv19 on 2009-02-05
I have a compaq Presario V6000, and I want to know if it is possible to install UNR remix on Ubuntu 7.10? Im trying to make my set up quick and simple, like the new Asus Eee Pcs with the simple layout. Thanks

---

### Post by snowpine on 2009-02-05
Hi Mitch,
I believe UNR is available for Hardy and Interpid only, according to this page: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

I would recommend upgrading to Hardy anyways, as Gutsy is reaching its "end of life" in 2 months and will no longer be supported.

---

### Post by mitchbv19 on 2009-02-05
Ok how do I upgrade? Will I lose the installed packages for my network card and soundcard that I installed separately? Do I have to uninstall Gutsy?

---

### Post by snowpine on 2009-02-05
Upgrading is easy, and theoretically it is a seamless process (you shouldn't lose documents or settings). However, here are my tips before upgrading:

1. Back up your important documents, just in case!
2. Test 8.04 on your hardware using an 8.04 Live CD. Basically you are checking to make sure 8.04 runs okay on your system.

OK, assuming 8.04 worked fine, you're ready to upgrade. Go back to 7.10 and then upgrade from System->Administration->Update Manager, as described here: [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

That should upgrade you to Hardy, good luck!

---

### Post by mitchbv19 on 2009-02-05
I see where it says to upgrade in the update manager. Why does it say 8.04 and not 8.10? Do I need to backup the packages for the network card?

---

### Post by snowpine on 2009-02-05
You can't skip from 7.10 to 8.10; you'd have to go to 8.04 first and then 8.10. I can't recommend between 8.04 and 8.10; it's really up to you. Both are fully supported. 8.10 is newer, obviously, but 8.04 is a long-term-support version (through April 2011), so they both have pros and cons.

It's possible you might have to reconfigure your network after the upgrade, I'm really not sure without knowing the details... when in doubt, back it up!

---

### Post by mitchbv19 on 2009-02-05
Does Gutsy 7.10 have a folder that I can backup and save my added in wireless card information.

---

