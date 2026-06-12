---
title: "Program Uninstall"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by uraykah on 2009-09-30
Hi.. I want to Uninstall thunderbird.. 

Installed it a couple of months back (2.0.0.21) using a tar.gz file because that was a newer version than the one listed in synaptic.. Now I'm not able to unistall it. Its not listed as installed in either synaptic or add\remove programs.. and apt-get remove says that program isn't installed.

Can anyone help

Thanks!

---

### Post by ErikEhlert on 2009-09-30
What distro of linux are you running and what version?

You should have an add/remove programs or program manager of some sort in linux.

---

### Post by Lars Noodén on 2009-10-01
Manual installation bypasses the package manager database.  So packages installed that way will not be accessible via the package manager.  

I learned the hard way not to mix and match.

What you might be able to do to repair things right now, (first back up your system) is download the tarball for the version you installed manually.  Do all the steps except 'make install'  then look at the script to see which files 'make install' copies and to where.  Zap them.

What you can do when wanting to go past the bleeding edge is roll your own package from the tarball and then install that.  The endnotes in the article below point to how to do it:
  [http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/)

If you keep your notes and the spec file, the second time you do it, it is very, very easy.

---

