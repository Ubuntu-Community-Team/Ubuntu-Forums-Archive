---
title: "installing Qucs on 12.10"
date: 2012-12-28
forum: Hardware
---

### Post by ariskk on 2012-12-28
I am trying to install Qucs on ubuntu 12.10 but I can't due to the missing libqt3. Qucs is not available via the software center and I've downloaded the source code. I've managed to install a couple of dependencies but now ./configure fails at

...
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for Qt headers... found in /usr/include/qt3
checking for Qt... 3 (multi-threaded)
checking for Qt library... configure: error: not found

Any idea how to proceed from this point on?

Thanks

---

### Post by phxfreddy@hotmail.com on 2013-03-08
> **ariskk said:**
> I am trying to install Qucs on ubuntu 12.10 but I can't due to the missing libqt3. Qucs is not available via the software center and I've downloaded the source code. I've managed to install a couple of dependencies but now ./configure fails at

...
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for Qt headers... found in /usr/include/qt3
checking for Qt... 3 (multi-threaded)
checking for Qt library... configure: error: not found

Any idea how to proceed from this point on?

Thanks

I had the same issue.  You are not using the mt libs. ( multithreaded )  See my note page here:  [http://www.amarketplaceofideas.com/design-tools/circuit-analysis/qucs-circuit-simulator/qucs-build-notes](http://www.amarketplaceofideas.com/design-tools/circuit-analysis/qucs-circuit-simulator/qucs-build-notes)

Problem: After building the Qt library the ./Configure choked at the point it was supposed to find the library.   This must have been because of it being the non threading library because of this:
Though the QTDIR environment variable is setup correctly, it may happen that the configure script cannot find the Qt® libraries because it is initially looking for the threaded libraries (the libqt-mt.so link). If you have installed the non-threaded library (the libqt.so link) configure fails. This can be worked around by

	$ ./configure --disable-mt   

AND THIS WORKED

---

