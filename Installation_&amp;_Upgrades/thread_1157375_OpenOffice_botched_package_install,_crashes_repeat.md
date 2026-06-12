---
title: "OpenOffice botched package install, crashes repeatedly"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Kareeser on 2009-05-12
Hey guys,

Usually, I update my OpenOffice.org installation by uninstalling OpenOffice:
sudo apt-get remove openoffice*

... and downloading the Linux DEB straight from OpenOffice.org and installing it.

This time around, I added the [OpenOffice.org PPA](https://launchpad.net/~openoffice-pkgs/+archive/ppa), just for kicks, and installed it. Unfortunately, I left openoffice.org running, and that might have messed around with some things.

Long story short, I tried to uninstall openoffice.org using the same method as described above, except now, dpkg reported that it _couldn't find the package_, even though I hadn't altered my software sources. Eventually, I went into Synaptic and got trigger happy with the openoffice packages, and removed any I could find.

**THEN**, I tried to install the Linux DEB, which proceeded fine. Only problem now being that the program won't actually run properly. When I click on the button to open a new document, OO crashes and throw up an error submission dialogue.

I've tried "sudo apt-get purge openoffice*", followed by autoremove and autoclean, but nothing has changed.

Help!

---

### Post by sir_nasty on 2009-05-12
what's the message when it crashes?

---

### Post by whoop on 2009-05-12
Did you remove ~/.openoffice.org ?

---

### Post by Kareeser on 2009-05-12
Beautiful. I thought apt-get purge would have erased ~/.openoffice, but I guess not!

Too bad UF doesn't have karma, you just earned some there.

---

