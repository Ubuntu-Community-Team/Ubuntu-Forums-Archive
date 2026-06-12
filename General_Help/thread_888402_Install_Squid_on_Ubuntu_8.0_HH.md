---
title: "Install Squid on Ubuntu 8.0 HH"
date: 2008-08-13
forum: General Help
---

### Post by gpb on 2008-08-13
New to all of this!!! I would like to install squid on my Ubuntu 8 HH Server box. I have downloaded the Squid (tar.gz) file from the ubuntu package website. I have burnt the tar.gz downloaded file to cd. I have successfully mounted my cd and given the command:

 “sudo aptitude install squid squid-common”

System tells me it cannot find the package squid. How do I go about installing squid successfully after I have downloaded the TAR.GZ file????? And burnt CD. Please help.

---

### Post by justleen on 2008-08-13
what did the tarball contain? a .deb file?

---

### Post by justleen on 2008-08-13
squid is in the repositories?
```

apt-get update
apt-get install squid squid-common 
```

---

