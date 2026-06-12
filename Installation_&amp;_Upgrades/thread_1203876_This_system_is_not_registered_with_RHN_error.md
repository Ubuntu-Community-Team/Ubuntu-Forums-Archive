---
title: "This system is not registered with RHN error"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by arvind.laddu on 2009-07-03
I have installed yum correctly through createrepo rpm...
but whenever i install nething from yum it shows a message that 
This system is not registered with RHN 
I am prepairing for RHCE plz help me..
Thanks

---

### Post by cariboo on 2009-07-04
Ubuntu doesn't use yum, so I really doubt it will work. To install programs from the command line use apt-get. If you are a new user I would suggest using Add/Remove Applications or Synaptic Package Manager.

Ubuntu is based on Debian which uses .deb packages. Redhat, OpenSuse and others use .rpm, that normally do not install properly on an .deb based system.

If you are preparing for the RHCE, you should be using RedHat or Fedora.

---

### Post by low351 on 2010-08-17
To late for him but I imagine he found his answer, If he was getting that message he was probably using RedHat and just posted here mistakenly, but for those who follow...

I believe this would have been the answer he was looking for:

run yum with the --noplugins option so yum will not try to communicate with the Red Hat Network servers to fetch the package and its dependencies

---

