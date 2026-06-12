---
title: "/home on server, install question"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by tparker on 2009-02-15
I am getting ready for a fresh install of 8.10 on a new (currently Vista) computer, no dual boot. My /home directory already exists on a local network server and I want to keep that as my home directory for the new install. 

Is there anything special I need to do during the install process to be sure that the account it creates at install (with all the permissions, sudo, etc.) accesses the network /home instead of making a local one?

Last time I tried this I had an access/permissions nightmare with the made-on-install sudo user and got errors telling me to give it permissions it already had. By the time I gave up my symlinks could have been mapped like a five highway interchange.

I ended up having to redo the install, make a new user, give them permissions, tie them to my network /home, then try to erase as much as I could of the made-on-install sudo user account to get the new user set up and able to access the network /home, but I always had errors and access/permissions problems. I do not want that to happen again so I am asking before the install this time to try and head off problems. :)

---

