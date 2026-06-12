---
title: "Downgrade xorg to hardy"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by ravi.xolve on 2009-03-30
I am really irritated with 8.10's x.org . The compiz or Kwin effects which used to work fine earlier no do not work at all on my Intel 845 motherboard.

I have an alternate disc of 8.04 too with all packages in .deb format. How can I use it to downgrade to hardy's X.org. I tried adding cdrom in synaptic and then checking the Hrady's packages section but I can't figure out how to downgrade.

Please tell me how to do it.

P.S.: I can manage the package dependencies. After all if something is broken i can re-install using apt-get from command line.

---

### Post by lykwydchykyn on 2009-03-30
In synaptic you can go to the package menu and "force version".  This can be tricky to do, though, if you have a package with other packages depend on.  It may be easier to temporarily disable the Intrepid repositories and downgrade.  You'll want to pin the version.

I have no idea what effect this will have on your system stability overall, but that's how you'd accomplish it.

---

