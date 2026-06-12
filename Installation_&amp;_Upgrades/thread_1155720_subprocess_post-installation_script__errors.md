---
title: "subprocess post-installation script  errors"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by punong_bisyonaryo on 2009-05-11
I had installed Jaunty a few days ago. And after install, the update-manager popped up offering several updates. I updated my system, but there were some "subprocess post-installation" problems, although I could install other programs just fine.
My errors were the following:

```
Setting up synaptic (0.62.5ubuntu3) ...
Segmentation fault
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.26.1-0ubuntu1) ...
Segmentation fault
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-netbook-remix:
 ubuntu-netbook-remix depends on evince; however:
  Package evince is not configured yet.
 ubuntu-netbook-remix depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing ubuntu-netbook-remix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-applets-data (2.26.1-0ubuntu1) ...
Segmentation fault
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-system-tools (2.22.2-0ubuntu4) ...
Segmentation fault
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ubuntu-docs (9.04.10) ...
Segmentation fault
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.26); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.27); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 synaptic
 evince
 ubuntu-netbook-remix
 jockey-gtk
 gnome-applets-data
 gnome-system-tools
 ubuntu-docs
 gnome-applets
 update-manager
 software-properties-gtk
 apturl
 language-selector
 gnome-app-install
```

Then I found through [http://ubuntuforums.org/showthread.php?t=590812](http://ubuntuforums.org/showthread.php?t=590812) that if I removed /var/lib/scrollkeeper/scrollkeeper_docs it might work again. And it did. Funny thing is this problem and solution came all the way back from Feisty.
I hope this helps someone out there.

---

