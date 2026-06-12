---
title: "Perl problem - GCstar Installation"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by srinath1905 on 2008-12-28
Hi all,

I was trying to install GCstar 1.4.3 from a DEB file I got from GetDeb. When I double click on it it says

> error: Cannot install 'libarchive-tar-perl'

When I try to install libarchive-tar-perl via apt it says this

> Reading package lists... Done
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
  libarchive-tar-perl: Depends: perl (>= 5.6.0-16) but it is not going to be installed
                       Depends: libio-zlib-perl
E: Broken packages


I am able to install GCstar 1.3 from the repos just fine using apt. I am using Intrepid Ibex. Any suggesstions?

---

