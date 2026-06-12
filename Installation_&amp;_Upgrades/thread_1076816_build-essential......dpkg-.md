---
title: "build-essential......dpkg-"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by rimig88 on 2009-02-21
So I am trying to install build-essential...

This is what I get...

```
sudo apt-get install build-essential
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
  build-essential: Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

```

So it looks like I need to install "dpkg-dev" right?

```
sudo apt-get install dpkg-dev
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
  dpkg-dev: Depends: dpkg (>= 1.13.1) but it is not going to be installed
E: Broken packages
```

So I need to install "dpkg"??


```
 sudo apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now What??

It seems like I have it installed already but it's complaining when I try to install build-essential.....any ideas?

---

