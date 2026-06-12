---
title: "trouble updating via update manager..."
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2009-02-10
hi there,

I am running ubuntu 8.10 on XPS 1330.

When I try to update through update manager for updates I keep getting the message below;

```
GPG error: http://au.archive.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

I am my uni´s superfast internet and everything is working ok except that little thing.

How do I go about fixing this gentleman?

---

### Post by Partyboi2 on 2009-02-11
Go to Software Sources (System>Admin>Software Sources) and on the first tab make sure the option to use cdrom as installable medium is unticked.

---

