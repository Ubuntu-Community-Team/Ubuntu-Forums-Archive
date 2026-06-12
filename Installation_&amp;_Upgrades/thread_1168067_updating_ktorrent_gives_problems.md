---
title: "updating ktorrent gives problems"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by skatebiker on 2009-05-23
When I try to update ktorrent with 

sudo apt-get install ktorrent

I got this error message:


[FONT="Courier New"]ktorrent:
  Depends: kdebase-runtime (>=4:4.1.96) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed
  Depends: kdelibs5 (>=4:4.1.96) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed
  Depends: kdepimlibs5 (>=4:4.2.0) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed
  Depends: libphonon4 (>4:4.3.0) but 4:4.2.0-0ubuntu1 is to be installed
  Depends: phonon (>4:4.3.0) but 4:4.2.0-0ubuntu1 is to be installed
[/FONT]

Running apt-get update or apt-get -f install does not help.

How can I install these missing libraries ?

---

