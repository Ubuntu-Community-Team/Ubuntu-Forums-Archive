---
title: "untrusted kernel package"
date: 2008-10-13
forum: General Help
---

### Post by frank05 on 2008-10-13
When trying to run aptitude dist-upgrade on my brand new dell laptop, i get the following message:

```

WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  linux-ubuntu-modules-2.6.24-19-generic 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": 

```

To me this says that either this package is not correctly signed (in which case I need to make a bug report) or I am missing the public key of some package maintainer (in which case i need to install it with apt-key). I am using the standard set of repositories that came preinstalled on my dell.

Could someone explain how to track down where this package comes from? (i.e. which server and which suite (main, universe, etc)). If I can do this maybe I can either file a bug report or download and install the required public keys.

I think this maybe a package pointing to some dell specific package (special closed source drivers maybe!?), which might complicate matters.

Thanks,

---

### Post by geirha on 2008-10-13
I believe it should've been signed with key 437D05B5, and I think you can get that message if apt for some reason failed to get the file with the signature for that package.

Try changing to a different mirror to see if you get the same error.

```
aptitude show linux-ubuntu-modules-2.6.24-19-generic
``` will show some information on the package.

---

