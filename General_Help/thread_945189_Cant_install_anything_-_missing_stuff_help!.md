---
title: "Cant install anything - missing stuff help!"
date: 2008-10-12
forum: General Help
---

### Post by hatboysam on 2008-10-12
I just did a fresh ubuntu install today and the only thing i have changed is I did a very thorough mac theme (including gnome menu bar applet if it matters)
There are multiple things i want to install but every time i try I get th e following:

> 
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome2-globalmenu-applet: Depends: gnome-common but it is not going to be installed
                            Depends: gnome-pkg-tools but it is not going to be installed
                            Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  gtk2-engines-pixbuf: Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4 is to be installed
                       Depends: libglib2.0-0 (>= 2.16.0) but 2.14.1-1ubuntu1 is to be installed
                       Depends: libgtk2.0-0 (= 2.12.9-4ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
                       Depends: libpango1.0-0 (>= 1.20.1) but 1.18.2-0ubuntu1 is to be installed
  gtk2.0-examples: Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4 is to be installed
                   Depends: libglib2.0-0 (>= 2.16.0) but 2.14.1-1ubuntu1 is to be installed
                   Depends: libgtk2.0-0 (= 2.12.9-4ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
                   Depends: libpango1.0-0 (>= 1.20.1) but 1.18.2-0ubuntu1 is to be installed
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.12.0-1ubuntu3.1) but 2.12.9-4ubuntu3 is to be installed
               Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  libgtk2.0-bin: Depends: libgtk2.0-0 (>= 2.12.9-4ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libxrandr-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
                 Depends: libxcomposite-dev but it is not going to be installed
                 Depends: libxdamage-dev but it is not going to be installed




It tells me to a "apt get -f install" but that just wants to delete everything

What do i need to do?

---

### Post by earthpigg on 2008-10-12
> **hatboysam said:**
> I just did a fresh ubuntu install

...

It tells me to a "apt get -f install" but that just wants to delete everything

What do i need to do?

from google searching 'man apt-get' on this windows computer:


> -f 
--fix-broken 
Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. **The option is sometimes necessary when running APT for the first time;** APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(8) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken. 

interesting... the install you did went perfect, no hitches or weirdness during install?

---

### Post by hatboysam on 2008-10-12
> **earthpigg said:**
> from google searching 'man apt-get' on this windows computer:




interesting... the install you did went perfect, no hitches or weirdness during install?

Sorry if I'm being dumb, but I'm not sure what you just told me to do.
The install went fine.
I have a sneaking suspicion that the gnome menubar thing i installed is the problem, but attempting to add or remove anything gives me that feedback.  If i do apt-get -f install, it will install all of those needed things but removed 726 M of other things, which is exactly what i did that caused me to need the reinstall.

---

### Post by earthpigg on 2008-10-12
im not telling you to do anything, just observing... im no expert, and i have no idea what the consequences could be of doing the -f thing.

however, any reason you dont just say "screw it" and do the -f thing it wants you to do? clean install means nothing to lose :)

---

### Post by hatboysam on 2008-10-12
because doing what the "f thing" wants me to do was exactly what made me have to reinstall

---

