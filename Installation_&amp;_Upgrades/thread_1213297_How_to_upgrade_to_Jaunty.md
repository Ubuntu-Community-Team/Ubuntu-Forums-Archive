---
title: "How to upgrade to Jaunty?"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2009-07-14
My sister is using Ubuntu 8.x, and would like to upgrade to Jaunty.  We've downloaded and burned the CD, but there doesn't seem to be an option to ugrade an existing Ubuntu installation, just "nuke, pave and rebuild."  What's the best way to upgrade?

---

### Post by drs305 on 2009-07-14
Here is the Ubuntu wiki that provides good updating information:

[JauntyUpgrades]("https://help.ubuntu.com/community/JauntyUpgrades")

I believe the Alternate CD allows upgrading a release, or you can opt for an online update or clean install. It also makes a difference if she is upgrading from 8.04 or 8.10. The wiki will provide all her options.

---

### Post by sideburns on 2009-07-14
Thanx, but that didn't work.  Of course, she might not be using the version I think she is; how can we tell?

---

### Post by unlimitedz on 2009-07-14
open a terminal and run
cat /etc/*release

---

### Post by sideburns on 2009-07-14
8.04.  After using the Software Updater to update everything, we checked again and there was nothing about a version upgrade for Ubuntu itself.

---

### Post by unlimitedz on 2009-07-14
Go to System-Administration-Software Sources.  Click on "Update" tab, then for "Release Upgrade" select "Normal Releases".  Then try your software update.

---

### Post by drs305 on 2009-07-14
> **sideburns said:**
> 8.04.  After using the Software Updater to update everything, we checked again and there was nothing about a version upgrade for Ubuntu itself.

In Synaptic > Settings > Repositories, Updates tab she can elect to display the type of online upgrades she wishes. She would have to select "Normal releases" in the "Release Upgrade" section. The default I think is Long-term Support releases only, which if not changed would not show the option to upgrade to 8.10.  She could do an online/network update to 8.10 and then again to 9.04 if she wants to go this route.

---

### Post by raymondh on 2009-07-14
Upgrade from Hardy to [Intrepid]("https://help.ubuntu.com/community/IntrepidUpgrades")

intrepid to [jaunty]("https://help.ubuntu.com/community/JauntyUpgrades")

Good luck.

---

