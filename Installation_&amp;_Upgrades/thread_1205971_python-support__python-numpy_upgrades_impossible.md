---
title: "python-support / python-numpy upgrades impossible?"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by washakie on 2009-07-06
Hello,

I'm trying to upgrade my python-numpy version to 1.3

It has caused me a load of troubles. If I manually install v1.3, it is only recognized once I uninstall python-numpy using apt-get or any other package manager.

That, however, causes a host of other packages to be removed as a result of dependencies... (I guess apt-get or aptitude - i've tried both) doesn't recognize the numpyV1.3 manual installation...)

I also had some issues where python-support was needing to be upgraded, and this seemed hopeless as well. I removed that, trying to do a manual installation as well, and ... let's just say I'm glad I'm not completely reinstalling the OS, what a mess!

################## EDIT #########################
The situation was solved over on the numpy board:

> I ran into this same problem a few days ago. The issue is that Python
imports from /usr/python2.6/dist-packages before
/usr/local/python2.6/dist-packages causing your numpy 1.3 (assuming its
installed there) to be hidden by the snaptic numpy.

To solve the problem, I added this line to my ~/.bashrc file:

export PYTHONPATH="${PYTHONPATH}:/usr/local/lib/python2.6/dist-packages"

replace the /usr/local/lib/python2.6/dist-packages with whatever directory
you installed your numpy 1.3 in. This path will be imported before any of
the other standard directories.


---

