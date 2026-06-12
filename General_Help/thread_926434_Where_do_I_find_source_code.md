---
title: "Where do I find source code?"
date: 2008-09-21
forum: General Help
---

### Post by compnut41 on 2008-09-21
Where is the best place for me to find the source code for my apps?

---

### Post by OutOfReach on 2008-09-21
The source code should be able to be downloaded from the project's site. (Usually in .tar.gz format)

---

### Post by niteshifter on 2008-09-21
Hi,

> The source code should be able to be downloaded from the project's site. (Usually in .tar.gz format)

Er ... yes and no. Some packages are "tweaked" for Ubuntu, the original sources may or may not match what's installed from the repositories.

To get the source for a repository package, specific version:
```
apt-get source *<package=version>*
```

To get the *latest* source:
```
apt-get source *<package>*
```

Either way, the source will be downloaded to the current working directory.

---

