---
title: "python2.4-pam"
date: 2005-12-01
forum: General Help
---

### Post by mikearagua on 2005-12-01
Hi,

I recently switched a server over from orthodox debian over to Ubuntu 5.10.  Most things seem to work fine but for whatever reason the python2.4-pam package doesn't seem to function as expected.  When I run the pamtest.py in the /usr/share/doc/python2.4-pam/examples directory and enter my username/password it says "authentication failed".  I think this is an issue with the ubuntu version of the package but maybe I'm missing a package or something.  Has anyone else been able to get it working on Ubuntu 5.10 x86?

Thanks

---

### Post by mikearagua on 2005-12-05
nevermind, it was a problem with permissions on /etc/shadow

forgot to change those.

---

