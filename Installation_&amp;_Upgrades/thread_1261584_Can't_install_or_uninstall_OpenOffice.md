---
title: "Can't install or uninstall OpenOffice"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by DaveDixon on 2009-09-08
64-bit Jaunty: Every time I try to add or remove an application from GNOME:Applications:Add/Remove I get "E: openoffice.org-writer2latex: subprocess post-installation script returned error exit status 127"

Despite the error, the package is successfully installed/uninstalled, except OpenOffice itself. It can be uninstalled and re-installed, but the applications don't run. They fail silently.

If I do sudo dpkg --configure -a, I get

Setting up openoffice.org-writer2latex (0.5-8ubuntu1) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg.../var/lib/dpkg/info/openoffice.org-writer2latex.postinst: 18: /usr/lib/openoffice/program/unopkg: not found
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-writer2latex; however:
  Package openoffice.org-writer2latex is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-writer2latex
 openoffice.org

---

### Post by mikewhatever on 2009-09-09
Try running **sudo apt-get install -f** from Terminal.

---

### Post by Hagar Delest on 2009-09-09
Else, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by community nerd on 2009-09-09
Try the synaptic package manager and search the *open office metapackage.*

---

### Post by DaveDixon on 2009-09-18
Here's the output from sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openoffice.org-writer2latex (0.5-8ubuntu1) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg.../var/lib/dpkg/info/openoffice.org-writer2latex.postinst: 18: /usr/lib/openoffice/program/unopkg: not found
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-writer2latex
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by DaveDixon on 2009-09-18
The problem with installing the Sun OOo is that I can't fully remove the previous OO (see preceding post). I can *mostly* remove it, but I'm a little scared of what will happen when I try to install Sun's OO over a partially removed Ubuntu OO. How bad could it be :confused:

---

### Post by DaveDixon on 2009-09-18
Sun OpenOffice did the trick. Thanks!

---

