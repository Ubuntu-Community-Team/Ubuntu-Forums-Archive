---
title: "Download .deb from apt-get"
date: 2008-11-11
forum: General Help
---

### Post by podollb on 2008-11-11
How do I download a .deb package using apt-get? I see the man page for apt-get seems to have --download-only and --compile to get the .deb from apt-get but I don't know how to get that to work. I've installed a few very large packages via apt-get install and I'd like to just grab the .deb so that future installs are as painful waiting for the network to download the package.

---

### Post by johanhartman on 2008-11-11
have you tried;

```
sudo apt-get install -d "package"

```

---

