---
title: "gimp-print wants to remove gimp"
date: 2008-09-26
forum: General Help
---

### Post by barna on 2008-09-26
Can anybody tell me, why the package gimp-print wants to remove the packages gimp, pandora, gimp-python? (Ubuntu 7.10)
It seems to me that Ubuntu is seriously degrading in terms of package management, dependencies, etc. This is not the first time that two packages ar conflicting. Or did I screw up something?

---

### Post by Pro-reason on 2008-09-26
Have you enabled any extra repositories?

---

### Post by barna on 2008-09-26
I have the following repositories enabled:
Ubuntu software:
  Canonical-supported open source software (main)
  Community-maintained open source software (universe)
  Proprietary drivers for devices (restricted)
  Software restricted by copyright or legal issues (mutiverse)
  Source code
Third party software:
  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner (Source Code)
  [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

I had also [http://repository.akirad.net/](http://repository.akirad.net/) akirad-gutsy. I have disabled this repository, it did not change anything. 

Can this be the reason? These gimp packages seem to be on trusted repositories (ubuntu, canonical), so I trusted that this set of repositories is ok.

Thanks for any hint. There was also a similar problem with libgimp-perl (which also other people reported...)

---

### Post by Pro-reason on 2008-09-26
As far as I can tell, that repo has no conflicting packages.

I can't reproduce that error, because I'm on Hardy Heron.  I presume that the packagers updated one part of the GIMP, and not another, so there is a clash.  You could try waiting a bit until the problem is corrected.  You could also [report it as a bug]("https://bugs.launchpad.net/ubuntu/").

---

