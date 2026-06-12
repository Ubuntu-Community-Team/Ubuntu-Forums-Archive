---
title: "dpkg problem with openoffice"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Abhijit Navale on 2009-07-19
i have ubuntu studio 9.04 on compaq presario a965tu laptop
after updating ubuntu i try to install openoffice but at the end of installation it frezes 
then i restart computer
synaptric package manager in not starting saying E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when using 'Add/Remove' utility to remove the openoffice then same error
also when installing any other software then also same error

any solution??
or any way to forcefully remove openoffice? (will if solve problem)?

is it wise now to switch back to 8.04?

---

### Post by ibutho on 2009-07-19
Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```

---

### Post by Abhijit Navale on 2009-07-19
i typed
sudo dpkg --configure -a
into the terminal then it says

Setting up openoffice.org-writer2latex (0.5-8ubuntu)...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pk
g...

then the whole system hangs
cannot open new application
currently opened application do not work

i have to forcefully shutdown and then start the pc

---

### Post by Abhijit Navale on 2009-07-24
does it happens due to swap partition. bcase I dont have swapt partition. so is it affecting it?

---

### Post by DaveDixon on 2009-08-29
I'm having a similar problem: Every time I try to add or remove an application from GNOME:Applications:Add/Remove I get "E: openoffice.org-writer2latex: subprocess post-installation script returned error exit status 127"

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

Is there any hope?

---

