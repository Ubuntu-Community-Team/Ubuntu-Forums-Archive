---
title: "Alternate Options for Upgrade via Local Repo"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by BadServo on 2009-10-29
I run an internal local repository for Ubuntu updates.  Approximately 30 workstations and servers use this repository for updates.

Sadly, as has been reported many times before, the Ubuntu upgrade scripts ignore your original apt sources and use known official Ubuntu mirrors, whihc can take ages, especially right after release.  In searching for a solution to this problem, I stumbled upon the following thread:

[http://ubuntuforums.org/showthread.php?t=763925&highlight=upgrade+local+repo](http://ubuntuforums.org/showthread.php?t=763925&highlight=upgrade+local+repo)

While I'm sure this would work, it worries me to rely on such a script that modifies installation/upgrade instructions.  I fear that future versions of the meta-release files might not work correctly with the script.

As such, I'm wondering if there is a simpler, purely client side solution to speedier upgrades.  My initial thought would be a simple script that would download the needed upgrade packages from the local mirror to the client.  At that point, you could kick off the normal installer and even though it relies on the official mirrors, one would not have to worry about download times, since most packages would be precached on the client already.

Any ideas, alternatives, or insights are appreciated.

---

