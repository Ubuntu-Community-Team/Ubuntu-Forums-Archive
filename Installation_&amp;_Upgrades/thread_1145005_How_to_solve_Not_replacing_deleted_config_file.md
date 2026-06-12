---
title: "How to solve: Not replacing deleted config file?"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Siebren on 2009-05-01
I think I screwed my installation of R, and I do not seem to be able to get it back to normal. I had been playing around with libraries inside R, and I got some weird dependency problem inside R. That is not what my question is about.

I then decided to reinstall R. Which did not help, so I thought the configuration files might be the problem. I then purged R, and got the warning that /etc/R was not deleted because it was not empty. I then deleted that directory (bad mistake?).
Now when I install, I keep getting:
Not replacing deleted config file /etc/R/Renviron

Any variation of aptitude/apt-get install, purge, clean etc does not seem to work
sudo dpkg--reconfigure does not seem to work (including flags such as --force)
sudo dpkg -P does not seem to work

Is there an explicit command to reconfigure a package, discarding all previous configurations?
Or is there an explicit command for a package to forget that a file was deleted? I would assume that it is somewhere stored that the configuration files were deleted, even though I have purged the associated packages.

thanks in advance

---

### Post by Frozsyn on 2009-05-01
Have you tried to "purge" the package, and then reinstall it ? To purge a package means to delete it and its configuration files, so it seems to be related to your problem. Here are the possible commands:

```
aptitude purge pkg-name
```
or
```
apt-get purge pkg-name
```

---

### Post by Siebren on 2009-05-01
Hi Frozsyn,

As I said in my opening question, I tried:
sudo apt-get reinstall (all packages associated with R, about 20 of them)
sudo apt-get purge (all packages associated with R)

and I tried
sudo dpkg --reconfigure r-base-core (which is the package with the problem)
sudo dpkg -P --force r-base-core

and then reinstalling again.

---

### Post by StuartN on 2009-05-01
There may be a reference to the old conf file in /var/lib/dpkg/status for the package r-base-core - mine says:
```
Package: r-base-core
Status: install ok installed
Priority: optional
Section: math
Installed-Size: 31940
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: r-base
Version: 2.7.1-2
Replaces: r-base (<= 1.4.1-1), r-cran-rcompgen (<= 0.1-17-1), r-gnome (<= 2.3.1), r-recommended (<< 1.9.0)
Provides: r-cran-rcompgen, r-gnome
Depends: perl, zip, unzip, libpaper-utils, libblas3gf | libblas.so.3gf | libatlas3gf-base, libc6 (>= 2.8~20080505), libcairo2 (>= 1.2.4), libgfortran3 (>= 4.3), libglib2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libjpeg62, liblapack3gf | liblapack.so.3gf | libatlas3gf-base, libpango1.0-0 (>= 1.21.3), libpcre3 (>= 7.4), libpng12-0 (>= 1.2.13-4), libreadline5 (>= 5.2), libsm6, libtiff4, libx11-6, libxt6, tcl8.4 (>= 8.4.16-2), tk8.4 (>= 8.4.16-2), zlib1g (>= 1:1.2.3.3.dfsg), ucf
Recommends: r-recommended, r-base-dev
Suggests: ess, r-doc-info | r-doc-pdf | r-doc-html, r-mathlib, r-base-html | r-base-latex
Conflicts: r-cran-rcompgen, r-gnome
Conffiles:
 **/etc/R/Makeconf f9bb9ad1735db03c99bfd821da43f11a**
 /etc/R/repositories 587ce586666f797de9dcc285f4540406
 /etc/R/ldpaths f12ca56a64769eb508f39fa180cf3a67
 /etc/ld.so.conf.d/libR.conf 87d14f4d2b70e19c062d41ba903b9f47
 /etc/bash_completion.d/R cd2cad8b67e1b0c7d7b4ea55a0d7096c
Description: GNU R core of statistical computing language and environment
```

---

### Post by l0xin on 2010-08-29
> **Siebren said:**
> Hi Frozsyn,

As I said in my opening question, I tried:
sudo apt-get reinstall (all packages associated with R, about 20 of them)
sudo apt-get purge (all packages associated with R)

and I tried
sudo dpkg --reconfigure r-base-core (which is the package with the problem)
sudo dpkg -P --force r-base-core

and then reinstalling again.

Old thread, but it's the first on Google for this problem, so here's what worked for me :

```
apt-get --purge autoremove
```

The deleted config file mustn't be in the package you're purging, but a related/dependent one.

---

