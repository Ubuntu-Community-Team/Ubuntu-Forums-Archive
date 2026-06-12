---
title: "xlib install issue"
date: 2008-09-22
forum: General Help
---

### Post by j_70 on 2008-09-22
I am trying to install DB Designer, which needs the kylixlib which needs the xlib. I am in dependency hell. I have tried to install xlib and every time I try to install kylixlibs3-borqt_3.0-1_i386.deb I get a dependency error that xlib is needed. 

To install xlib, I have tried:

sudo apt-get install xlibs which says:

Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xkb-data

So installed xkb-data, but when I try to run kylixlibs3-borqt_3.0-1_i386.deb I still get the xlib dependency error. Red Hat ES is my normal OS so I am used to YUM resolving these issues for me. Thoughts?

---

### Post by phidia on 2008-09-22
From the homepage it looks like that program is still under development:
> DbDesigner is currently under development, but a first release is close. The project was started on April 28, but the effective development time was around 9 days (as of May 21). Watch the News section below for more details.

I doubt if YUM could resolve these issues since you're building from source-correct?
There would need to be a binary package (rpm or deb) for YUM or dpkg to install this and the dependencies.

Building from source very often has this dependecy crazy-making situation and that's across most all distros.

---

