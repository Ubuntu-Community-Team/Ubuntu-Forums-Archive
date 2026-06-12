---
title: "apt and adept commit errors"
date: 2008-07-21
forum: General Help
---

### Post by dhanes420 on 2008-07-21
Hello all:

I've a brand new 8.04.1 install of Kubuntu.  Have enabled the medibuntu repository.

Have tried with and without the medi repo to install several packages (Azureus, mythtv, mythtv-frontend, etc) and always get the "There was an error commiting changes.  Possibly .... or the commit would break packages."

About the only thing different than a standard stock install is the installation of nvidia-glx-new, succesfully. 

The mythtv-frontend, mythtv-backend and other plugins show install is fine, but won't install with the above error.  The mythtv install shows (BREAK: install) and of course all the dependants won't install with the meta install.

Any ideas?  Any info you might need to help me?

Thanx,

dhanes

edit: have done apt-get update and apt-get update -f

---

### Post by kuja on 2008-07-28
There's probably some sort of conflict dependency wise. That usually occurs when one package depends on a specific version of one package, and it's not available.

Third party repositories tend to suffer this more often than the official repository. If you've installed some of these from medibuntu you're stuck unless you can find out which ones they are and remove them and then install them again from the ubuntu repo.  Another option is to contact them to see and/or wait it out.

You can usually check which ones if any are installed from medibuntu by running this command in a konsole: ```
dpkg --list | grep ^ii.*medibuntu.*
```

---

### Post by dhanes420 on 2008-07-31
Weirdly enough....I manually changed some of the entries in sources.list to us.ubuntu.com from archive.ubuntu.com, got a 404 error, changed them back to archive.ubuntu.com and everything worked fine after that....

---

