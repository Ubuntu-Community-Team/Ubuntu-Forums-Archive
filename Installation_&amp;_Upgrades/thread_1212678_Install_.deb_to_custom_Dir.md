---
title: "Install .deb to custom Dir"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by RedSingularity on 2009-07-14
Title says it all......how can i install a .deb package to a directory of my choice such as a USB stick?  Even though i have been using linux for a while now i never figured out how to do it.  Any input would be helpful.

---

### Post by RedSingularity on 2009-07-15
B_u_m_p

---

### Post by Tibuda on 2009-07-16
Through the package manager, no.

What you can do is open the deb file in File Roller (the archive manager) and extract it, but it won't work if the dependencies are not installed.

---

### Post by az on 2009-07-16
> **Shadow121 said:**
> Title says it all......how can i install a .deb package to a directory of my choice such as a USB stick?  Even though i have been using linux for a while now i never figured out how to do it.  Any input would be helpful.

DPKG has this functionality built-in

sudo dpkg -i <package.deb> --root=/media/USBSTICK/

If you need to install a bunch of packages that all depend on each other, you list them all at the same time, separated by spaces.  The packages (.deb) need to be in the current directory since this does not use apt.

man dpkg


 --root=dir
              Changing  root  changes  instdir  to  dir and admindir to
              dir/var/lib/dpkg.


Now, this assumes that there is another Ubuntu system on that stick.  You can't install an arbitrary package to other directories than the ones that are specified in the package.  The shared libraries on an Ubuntu system have a very specific path.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by RedSingularity on 2009-07-16
That answers my question.  Thanks az.

---

### Post by loomsen on 2009-07-16
You may as well specify a prefix directory if you build from source...

just add --PREFIX=/path/to/dir to the configure option and the files will go there...

---

