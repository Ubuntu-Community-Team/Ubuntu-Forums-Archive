---
title: "Installing, Removing &amp; Keeping a clean system"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by Findarato on 2009-09-04
Hello everyone,

I would like to know how ubuntu handles install / remove programs. If I install / remove, is anything left behind ? I noticed the settings are often still present, is there anything else still on my system ?

Are there some ways to clean up your system (besides "Janitor" and autoremove) after a long time ?
I read multiple times Linux systems should never have to be re-installed, they get upgraded and cleaned up. Does that mean there are ways to clea it up as good as a new system ? If so, any tips ?

Thank you very much for your help,

Findarato

---

### Post by imhotep59 on 2009-09-04
To install or remove programs you can do this with synaptic which is a GUI for the command apt-get.
Synaptic will install the programs and its dependencies if needed.

You can also do this in a terminal with the following commands
- sudo apt-get install *name_of_the_package* (to install)
- sudo apt-get remove *name_of_the_package* (to remove)
- sudo apt-get remove --purge *name_of_the_package* (to remove the package and its configuration files)
- sudo apt-get autoremove --purge *name_of_the_package* (to remove the packages and its dependencies if they are no more useful)

When you install package they are first downloaded in your hard drive as .deb files. After installation these .deb files can be cleaned with :
- sudo apt-get clean (remove the .deb of the installed packages)
- sudo apt-get autoclean (remove the .deb of the disinstalled packages)

Hope it was helpful. For more information about apt-get you can ask for the man page (man apt-get) ou read the following link (if you speak french) :
[http://doc.ubuntu-fr.org/apt-get](http://doc.ubuntu-fr.org/apt-get)

---

