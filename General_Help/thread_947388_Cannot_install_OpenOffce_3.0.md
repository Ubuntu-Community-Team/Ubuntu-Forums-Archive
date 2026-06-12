---
title: "Cannot install OpenOffce 3.0"
date: 2008-10-14
forum: General Help
---

### Post by stevebond001 on 2008-10-14
Hi
I'm running Hardy and have just tried to install Openoffice 3.  When I try and install, the installation wizard appears and starts to install.  Then I get an error message stating:

 Package Name: ooobasis3.0-core04-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/ooobasis3.0-core04-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: libfreetype.so.6 is needed by ooobasis3.0-core04-3.0.0-9358.i586 Package Name: openoffice.org3-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: ooobasis3.0-core04 is needed by openoffice.org3-3.0.0-9358.i586 Package Name: ooobasis3.0-gnome-integration-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/ooobasis3.0-gnome-integration-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: libgnomevfs-2.so.0 is needed by ooobasis3.0-gnome-integration-3.0.0-9358.i586 libgconf-2.so.4 is needed by ooobasis3.0-gnome-integration-3.0.0-9358.i586 Package Name: openoffice.org3-writer-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-writer-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-writer-3.0.0-9358.i586 Package Name: openoffice.org3-calc-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-calc-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-calc-3.0.0-9358.i586 Package Name: openoffice.org3-draw-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-draw-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-draw-3.0.0-9358.i586 Package Name: openoffice.org3-impress-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-impress-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-impress-3.0.0-9358.i586 Package Name: openoffice.org3-base-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-base-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-base-3.0.0-9358.i586 Package Name: openoffice.org3-math-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-math-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-math-3.0.0-9358.i586 Package Name: openoffice.org3-en-US-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-en-US-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: openoffice.org3 is needed by openoffice.org3-en-US-3.0.0-9358.i586 Package Name: openoffice.org3.0-suse-menus-3.0-9354.noarch.rpm rpm --upgrade --ignoresize --force -vh /home/steve/Desktop/ooo/RPMS/desktop-integration/openoffice.org3.0-suse-menus-3.0-9354.noarch.rpm Returns: 1 Problem during installation. Can be ignored.  Package Name: openoffice.org3.0-mandriva-menus-3.0-9354.noarch.rpm rpm --upgrade --ignoresize --force -vh /home/steve/Desktop/ooo/RPMS/desktop-integration/openoffice.org3.0-mandriva-menus-3.0-9354.noarch.rpm Returns: 1 Problem during installation. Can be ignored.  Package Name: openoffice.org3.0-redhat-menus-3.0-9354.noarch.rpm rpm --upgrade --ignoresize --force -vh /home/steve/Desktop/ooo/RPMS/desktop-integration/openoffice.org3.0-redhat-menus-3.0-9354.noarch.rpm Returns: 1 Problem during installation. Can be ignored.  Package Name: openoffice.org3.0-freedesktop-menus-3.0-9354.noarch.rpm rpm --upgrade --ignoresize --force -vh /home/steve/Desktop/ooo/RPMS/desktop-integration/openoffice.org3.0-freedesktop-menus-3.0-9354.noarch.rpm Returns: 1 Problem during installation. Can be ignored.  Package Name: openoffice.org3-dict-en-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-dict-en-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: ooobasis3.0-core04 is needed by openoffice.org3-dict-en-3.0.0-9358.i586 openoffice.org3 is needed by openoffice.org3-dict-en-3.0.0-9358.i586 /bin/sh is needed by openoffice.org3-dict-en-3.0.0-9358.i586 Package Name: openoffice.org3-dict-fr-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-dict-fr-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: ooobasis3.0-core04 is needed by openoffice.org3-dict-fr-3.0.0-9358.i586 openoffice.org3 is needed by openoffice.org3-dict-fr-3.0.0-9358.i586 /bin/sh is needed by openoffice.org3-dict-fr-3.0.0-9358.i586 Package Name: openoffice.org3-dict-es-3.0.0-9358.i586.rpm rpm --upgrade --ignoresize -vh --relocate /opt=//opt /home/steve/Desktop/ooo/RPMS/openoffice.org3-dict-es-3.0.0-9358.i586.rpm Returns: 1 Error during installation  error: Failed dependencies: ooobasis3.0-core04 is needed by openoffice.org3-dict-es-3.0.0-9358.i586 openoffice.org3 is needed by openoffice.org3-dict-es-3.0.0-9358.i586 /bin/sh is needed by openoffice.org3-dict-es-3.0.0-9358.i586 

Does anyone know how to fix this?

BTW, I already have OpenOffice 2.4 installed and I have tried upgrading this installation with the update script supplied but nothing happens.

Many thanks in advance.

---

### Post by jespdj on 2008-10-14
Why are you trying to install it from an RPM package? Ubuntu (like Debian) uses DEB packages. Download the DEB package version instead of the RPM package version.

---

### Post by stevebond001 on 2008-10-14
jespdj
Thanks for the quick reply.  I have already tried the DEB package and ran the update script supplied with it.  I received the following output:

Skipping deselected package ooobasis3.0-writer.
Skipping deselected package ooobasis3.0-en-us-impress.
Skipping deselected package openoffice.org3-dict-en.
Skipping deselected package ooobasis3.0-math.
Skipping deselected package ooobasis3.0-xsltfilter.
Skipping deselected package ooobasis3.0-calc.
Skipping deselected package ooobasis3.0-base.
Skipping deselected package ooobasis3.0-ooolinguistic.
Skipping deselected package ooobasis3.0-en-us-writer.
Skipping deselected package openoffice.org-debian-menus.
Skipping deselected package ooobasis3.0-en-us-draw.
Skipping deselected package ooobasis3.0-en-us.
Skipping deselected package ooobasis3.0-core01.
Skipping deselected package ooobasis3.0-testtool.
Skipping deselected package ooobasis3.0-en-us-binfilter.
Skipping deselected package ooobasis3.0-en-us-help.
Skipping deselected package ooobasis3.0-impress.
Skipping deselected package openoffice.org3-math.
Skipping deselected package openoffice.org3-dict-es.
Skipping deselected package ooobasis3.0-kde-integration.
Skipping deselected package openoffice.org3-calc.
Skipping deselected package ooobasis3.0-core02.
Skipping deselected package ooobasis3.0-core03.
Skipping deselected package ooobasis3.0-pyuno.
Skipping deselected package ooobasis3.0-core07.
Skipping deselected package openoffice.org3-base.
Skipping deselected package openoffice.org3-writer.
Skipping deselected package ooobasis3.0-core04.
Skipping deselected package ooobasis3.0-en-us-res.
Skipping deselected package ooobasis3.0-core06.
Skipping deselected package ooobasis3.0-images.
Skipping deselected package ooobasis3.0-core05.
Skipping deselected package openoffice.org3.

Nothing else happens.  That's why I have tried the RPM package

Any suggestions?

Many thanks

---

### Post by kaibob on 2008-10-14
Here are a couple of HowTo's. I haven't tried them but the process seems fairly straightforward. 

[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros)

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by stevebond001 on 2008-10-14
Thanks Kaibob, I'll look at these in more detail later on.

---

### Post by kaibob on 2008-10-14
Please let us know how things go. I'm sure there are many forum members who are looking to upgrade to the new version.

---

### Post by russlar on 2008-10-14
if you have 64-bit Ubuntu/Kubuntu, use this link to get teh 64-bit debs: [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/)

---

### Post by scouser73 on 2008-10-14
Have you removed the previous version of OpenOffice? **sudo apt-get remove openoffice*.* ** [http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/")

---

### Post by stevebond001 on 2008-10-14
Thank you all very much - it worked.

What I did was:

1. sudo apt-get remove openoffice*.*
2. followed the instructions as per [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) 

And it just worked =D>

Hopefully this will help others with the same problem.

Thanks once agian.

---

### Post by 73ckn797 on 2008-10-14
See new thread of my installation success:

[http://ubuntuforums.org/showthread.php?p=5966220#post5966220](http://ubuntuforums.org/showthread.php?p=5966220#post5966220)

---

### Post by scouser73 on 2008-10-14
Here is instructions to install OpenOffice 3. [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/#comment-32248]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/#comment-32248")

I have just installed Intrepid Ibex, and it works a treat, this along with OpenOffice 3, nice one.

---

