---
title: "Documentation for Packages"
date: 2008-10-16
forum: General Help
---

### Post by aajax on 2008-10-16
One of the best features of Ubuntu is the huge repository of packages that can be installed.  Unfortunately I find it necessary to learn something about a package before deciding to install it.  Insofar as there are lots of packages that make similar claims with respect to capability there is a need for some depth.  The superficial paragraphs (or sentences) that show up in the package manager (e.g., Synaptic) are insufficient.

The amount of documentation available via the Ubuntu web site is extremely sparse when compared to the amount of sophistication that the system seems to possess.  While I suppose it is fair to say that documentation deficiencies are a common problem across all manner of information systems, it appears to be an especially acute problem for Ubuntu.

Having said that I really hope that I'm just plan wrong and that the problem is that I just haven't figured out where to find it.  If someone can enlighten me that would be great.

---

### Post by koenn on 2008-10-16
For a technical description of the package itself : [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For information about the actual program or programs packaged in the package : most open source programs have a dedicated website; look for the documenation there, or on one of the collection sites (freshmeat, sourceforge, ... )

---

### Post by geirha on 2008-10-16
Any documentation provided with a package is installed in /usr/share/doc/*packagename*/, but of course, you'll have to install it first before you can read it. 

A second option is to get the source of the package with ```
apt-get source *packagename*
``` There's usually some documentation there provided by the developer(s). Often in the README file or a doc-folder. 

The easiest way out is usually to search for it on the net. Find the homepage of the package ...

---

### Post by aajax on 2008-10-18
Many thanks.  I failed to find [http://packages.ubuntu.com](http://packages.ubuntu.com) from the home page.

---

