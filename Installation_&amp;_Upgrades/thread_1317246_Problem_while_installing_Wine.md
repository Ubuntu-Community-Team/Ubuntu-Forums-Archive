---
title: "Problem while installing Wine"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by The-NightPhoenix on 2009-11-06
I upgraded to Karmic Koala . after installing Wine 

this error keeps showing after trying to install any app


> 

--2009-11-06 22:24:38--  [http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)



is there any way to clear this post installation script or how can i solve this problem please

---

### Post by c/Kr3t on 2009-11-08
did you add the repository?

be sure it's added, checked on, and the authentication is there.

use this page to make sure it's all set up right.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by The-NightPhoenix on 2009-11-09
I Found the cause of the problem 

its the package "ttf-mscorefonts-installer" 
which downloads fonts for wine. appearntly there is a problem in the download of some kind so dpkg keeps trying to download them. 

i couldn't solve it , so i removed the package.

---

