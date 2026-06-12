---
title: "Jpilot-1.6.0: need help compiling/installing"
date: 2008-09-21
forum: General Help
---

### Post by davidpeace on 2008-09-21
I'm trying to install the latest jpilot because I had a problem with the version in the repos. When I type "make" I get an error that there is no target file or makefile. There is a Makefile.am and Makefile.in.

Has anyone had any luck with the latest jpilot?

---

### Post by mshumer on 2008-10-22
David,
I had the same problem you have. Fixed it this morning.

I downloaded the install .tar.gz from jpilot.org and tried to ./configure, it wouldn't.

Went to this page: [https://launchpad.net/ubuntu/intrepid/+source/jpilot/1.6.0-1](https://launchpad.net/ubuntu/intrepid/+source/jpilot/1.6.0-1) and looked at the contents of jpilot_1.6.0-1.dsc  (1.1 KiB) file.  (important part is next sentence)

It listed several dependencies; "Build-Depends: libpisock-dev (>= 0.12.2-11), gettext, libglib2.0-dev, libgtk2.0-dev, debhelper (>= 5.0.51~), libssl-dev, autotools-dev, libxml-parser-perl, libreadline5-dev"

I opened Synaptic package manager and made sure all the dependencies were installed (they weren't).

After that, _./configure_ and _make_ worked fine. Had to "sudo make install" and now, SUCCESS.

---

