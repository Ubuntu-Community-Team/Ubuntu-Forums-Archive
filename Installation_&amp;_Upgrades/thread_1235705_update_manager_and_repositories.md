---
title: "update manager and repositories"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2009-08-09
Hi there:

just now the OS announced my system is outdated, so I follow the given instructions to upgrade it. I go to the update manager, click check, and, just before ending the downloading, this is what appears:

The main message reads:

""Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.""

and then:

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

What do I have to do?

Cheers

---

### Post by oldos2er on 2009-08-09
Go to menus System, Administration, Software Sources, and uncheck the box next to 'Cdrom with Ubuntu....'

---

