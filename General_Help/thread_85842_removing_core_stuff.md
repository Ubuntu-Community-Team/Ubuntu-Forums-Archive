---
title: "removing core stuff"
date: 2005-11-03
forum: General Help
---

### Post by uberlinux on 2005-11-03
synaptic won't let me remove certain packages that came with the distro, is there a trick to this?
I says that if I remove something, that it will take a bunch of other crap with it.

---

### Post by aclaunch on 2005-11-03
That's the whole point of "dependencies"-one application/package depends on another. There are command line options to force a package to delete but you do so at your own peril. If something is "core" many other applications/packages that depend on it will probably break.

Alan

---

### Post by nagilum on 2005-11-04
If you really want to uninstall a package on which others depend you can do so with dpkg and the --force-depends option. This will ignore any problems with missing dependencies. But whenever you use apt-get (or synptic) it will reinstall the missing package, the --force option is not permanent.
To remove it permanently you have to create a dummy .deb with equivs. Equivs creates .debs which are basically empty packages you can give any name or version, i.e. allows you to fake the original package or create meta-packages (like gnome-desktop-environment).

But as aclaunch already said, this is some advanced stuff and can easily break your system. Do this only if you really know what you do.

---

### Post by Pimo on 2005-11-14
I have a related problem: I recently removed apache2 and mysql, because I use xampp... I DON'T want those packages, I don't need them, but the update manager bugs me all the time with the "updates".

Any ideas? :confused:

---

### Post by Pimo on 2005-11-14
Solved. The thing was that phpmyadmin couldn't be removed (broken package or something like that, helped by [http://www.ubuntuforums.org/showthread.php?t=79934](http://www.ubuntuforums.org/showthread.php?t=79934), so synaptic asked me for all the other stuff.

---

