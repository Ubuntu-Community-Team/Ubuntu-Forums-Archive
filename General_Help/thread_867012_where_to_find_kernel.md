---
title: "where to find kernel?"
date: 2008-07-22
forum: General Help
---

### Post by bro-ken on 2008-07-22
I understand I need a kernel specific to i686 32bit (amd duron 900mhz) I have no idea how to find compatible kernels, where to look, what to look for? help appreciated.

---

### Post by coffeecat on 2008-07-22
I'm fairly sure you don't need a specific kernel, the generic one installed by default should be fine for that processor. Or do you mean you want a 386 kernel? If you do need to install a different kernel, the installable packages are listed under linux-image-* in the package manager.

Are you about to install Ubuntu? Or just contemplating installing? Or have you already installed? If the live CD runs fine on your hardware, then it will install the appropriate kernel. If you have already installed and want to know which kernel is running, open a terminal and:

```
uname -r
```

You can do this when running the live CD as well.

---

