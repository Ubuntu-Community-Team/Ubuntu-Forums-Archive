---
title: "kdeplasma-addons removes digiKam"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by alingham on 2009-02-05
Hi
Came across a really annoying "feature" in KDE 4.2

To install any plasmoids worth having... you need to install the kdeplasma-addons. Unfortunately this seems to remove digiKam - one of the best photo managers and camera managers out there. A while ago FSpot stopped working for me... so I'm stuck.  I user plasmoids all the time, but I need digiKam to get the photos off my Canon camera.

Can anyone help!? Please???

This is what happens when I try and install digiKam after installing kdeplasma-addons:

user@darkness-x:~$ sudo apt-get install digiKam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  digikam kipi-plugins libkexiv2-3
Suggested packages:
  digikam-doc gallery kipi-plugins-doc
Recommended packages:
  kdeprint kooka
The following packages will be REMOVED:
  kdeplasma-addons libkexiv2-7
The following NEW packages will be installed:
  digikam kipi-plugins libkexiv2-3
0 upgraded, 3 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B/13.5MB of archives.
After this operation, 32.9MB of additional disk space will be used.
Do you want to continue [Y/n]? 

Hence if I install digiKam again, I will lose kdeplasma-addons...

---

### Post by putt1ck on 2009-02-06
You need Digikam 0.10 - add the repository as described here:

[https://launchpad.net/~digikam-experimental/+archive/ppa](https://launchpad.net/~digikam-experimental/+archive/ppa)

And note, rename your old digikam3.db file else the import process makes your photos not appear.

Oh, and tick all the upgrade boxes in your package manager else it won't install properly.

---

### Post by Materdaddy on 2009-02-23
Thanks for the help, but that solution doesn't work for me.  I added that repo and now I get the following:

```

$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  digikam: Depends: liblensfun0 (>= 0.2.3) but it is not installable
           Recommends: kipi-plugins but it is not going to be installed
E: Broken packages

```

If I try installing all 3 packages, I get no candidate for liblensfun0:

```

$ sudo apt-get install digikam liblensfun0 kipi-plugins
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package liblensfun0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package liblensfun0 has no installation candidate

```

Any other suggestions?

---

### Post by Materdaddy on 2009-02-23
Nevermind.  The link set the default repo to 'jaunty', which I figured was intentional for "experimental" packages.  I changed my apt entry to intrepid (since that's what I'm running) and it installed properly.  Thanks for the help!

---

