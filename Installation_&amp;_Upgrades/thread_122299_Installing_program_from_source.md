---
title: "Installing program from source?"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by TnT001 on 2006-01-27
How can I replace a program from the original ubuntu packages with a newer version, compiled from source. I know how to go through a "configure; make; make install" cycle, but I was wondering if this could cause some conflicts. If I do not install from a *.deb package, I loose the advantage of apt-get and friends? In case something goes wrong I would like to be able to return to the default package. How can I do this?

The program I would like to upgrade is dovecot (replace 0.99.14 with 1.0b2+).

---

### Post by MartinG on 2006-01-27
[QUOTE=TnT001]How can I replace a program from the original ubuntu packages with a newer version, compiled from source. I know how to go through a "configure; make; make install" cycle, but I was wondering if this could cause some conflicts. If I do not install from a *.deb package, I loose the advantage of apt-get and friends? In case something goes wrong I would like to be able to return to the default package. How can I do this?

The program I would like to upgrade is dovecot (replace 0.99.14 with 1.0b2+).[/QUOTE]If you install a package called checkinstall, then use a "configure; make; checkinstall" sequence, checkinstall produces a deb which is installed by dpkg (or apt), so that it is "registered" in the apt database.  You can check this after installation in synaptic, which has a status section called "installed (local or obsolete)".  It is therefore easy to uninstall the package and install another version.

(Using checkinstall you have to answer some questions, but the default answers are fine.)

---

