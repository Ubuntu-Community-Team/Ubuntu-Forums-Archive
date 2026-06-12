---
title: "Aptoncd alternative?"
date: 2008-10-09
forum: General Help
---

### Post by exus69 on 2008-10-09
Hi Everyone,

I was wondering if there's an alternative to aptoncd
package coz I dnt want to burn a cd or append to an existing
C.D all the time whenever a new package is available. Also 
is there any way if I can copy paste the downloaded .deb
packages from pen drive to archives folder so that they
are readily avaiable in the package manager. Right now
the copy paste isnt working in only that particular
archives folder. Am running Ubuntu 8.04.

Plz help,

Sunny

---

### Post by plucky on 2008-10-09
> **exus69 said:**
> Hi Everyone,

I was wondering if there's an alternative to aptoncd
package coz I dnt want to burn a cd or append to an existing
C.D all the time whenever a new package is available. Also 
is there any way if I can copy paste the downloaded .deb
packages from pen drive to archives folder so that they
are readily avaiable in the package manager. Right now
the copy paste isnt working in only that particular
archives folder. Am running Ubuntu 8.04.

Plz help,

Sunny


You need to be in super user mode to write to that directory but you can copy the .deb files to a pen drive without privileges.

Use ```
gksudo nautilus
``` to copy and paste the files from a pendrive to the **/var/cache/apt/archives** directory.


Good Luck

---

### Post by Irihapeti on 2008-10-09
You don't actually have to create a CD with APTonCD - you can create (and restore packages from) an .iso image.

Another way of storing packages is to have a personal repository. Details for setting one up are here: [https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)

Incidentally, I've found that some packages (mainly .debs I've created using Checkinstall) mess up the apt database.

---

