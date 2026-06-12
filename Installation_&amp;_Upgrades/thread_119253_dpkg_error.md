---
title: "dpkg error"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by WynD on 2006-01-19
Hi
everytime i try to install a package, I get this error

Errors were encountered while processing:
 zope2.7-portaltransforms
 zope2.7-archetypes
 zope-atrbw
 zope-atcontenttypes
 zope-cmfplone
 zope-ploneerrorreporting
 plone
 plone-site
 zope-plonelanguagetool
 zope-linguaplone
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm fairly new to Linux so I don't know what this is.
Thx for any help

---

### Post by WynD on 2006-01-19
here is what it said in terminal..

dpkg: error processing zope2.7-portaltransforms (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of zope2.7-archetypes:
 zope2.7-archetypes depends on zope2.7-portaltransforms (= 1.3.4-2ubuntu1); however:
  Package zope2.7-portaltransforms is not configured yet.
dpkg: error processing zope2.7-archetypes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-atrbw:
 zope-atrbw depends on zope2.7-archetypes (>= 1.3.1) | zope-archetypes (>= 1.3.1); however:
  Package zope2.7-archetypes is not configured yet.
  Package zope-archetypes is not installed.
dpkg: error processing zope-atrbw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-atcontenttypes:
 zope-atcontenttypes depends on zope2.7-archetypes (>= 1.3.1) | zope-archetypes (>= 1.3.1); however:
  Package zope2.7-archetypes is not configured yet.
  Package zope-archetypes is not installed.
dpkg: error processing zope-atcontenttypes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-cmfplone:
 zope-cmfplone depends on zope2.7-archetypes (>= 1.3.4) | zope-archetypes (>= 1.3.4); however:
  Package zope2.7-archetypes is not configured yet.
  Package zope-archetypes is not installed.
 zope-cmfplone depends on zope-atrbw (>= 1.1); however:
  Package zope-atrbw is not configured yet.
 zope-cmfplone depends on zope-atcontenttypes (>= 1.0); however:
  Package zope-atcontenttypes is not configured yet.
dpkg: error processing zope-cmfplone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-ploneerrorreporting:
 zope-ploneerrorreporting depends on zope-cmfplone (>= 2.0); however:
  Package zope-cmfplone is not configured yet.
dpkg: error processing zope-ploneerrorreporting (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plone:
 plone depends on zope-cmfplone (= 2.1-1); however:
  Package zope-cmfplone is not configured yet.
dpkg: error processing plone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plone-site:
 plone-site depends on zope-cmfplone (= 2.1-1); however:
  Package zope-cmfplone is not configured yet.
dpkg: error processing plone-site (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-plonelanguagetool:
 zope-plonelanguagetool depends on zope-cmfplone (>= 2.0.3); however:
  Package zope-cmfplone is not configured yet.
dpkg: error processing zope-plonelanguagetool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zope-linguaplone:
 zope-linguaplone depends on zope-cmfplone (>= 2.0.3); however:
  Package zope-cmfplone is not configured yet.
 zope-linguaplone depends on zope2.7-archetypes (>= 1.3.1); however:
  Package zope2.7-archetypes is not configured yet.
 zope-linguaplone depends on zope-plonelanguagetool; however:
  Package zope-plonelanguagetool is not configured yet.
dpkg: error processing zope-linguaplone (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zope2.7-portaltransforms
 zope2.7-archetypes
 zope-atrbw
 zope-atcontenttypes
 zope-cmfplone
 zope-ploneerrorreporting
 plone
 plone-site
 zope-plonelanguagetool
 zope-linguaplone
E: Sub-process /usr/bin/dpkg returned an error code (1)



"zope" is unconfigured.. how do i configure or install it?

---

### Post by MartinG on 2006-01-19
It looks to me as if you are trying to install using dpkg rather than apt-get? If that is the case, it's worth changing because apt-get sorts out dependencies automatically, unlike dpkg.

Leaving that aside, the first thing is to get your system back to a consistent state.  First, try ```
sudo dpkg --configure --pending
```, then run```
sudo apt-get update
sudo apt-get -s upgrade
```This last does a "dry run" of the upgrade process.  Check the last lines of the output to see if any packages are broken, held back or unconfigured.  If they are broken then remove and re-install them, if held back do likewise and do an upgrade and/or dist-upgrade, if unconfigured then run```
sudo dpkg-reconfigure <package-name>
```After all that, try again.  It seems a bit long-winded, but I think it should work.

Mind you, I prefer to use synaptic, as you can fiddle more before committing yourself:)

---

