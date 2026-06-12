---
title: "Appears OpenGL programs broken after update"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by Narclax on 2009-03-29
quick version: emulators/games do not work after update run


As most posts start out, thanks for even attempting to help.  I'm attempting to learn Ubuntu as I go along and have been doing well because of this forum up to this date.

I'm running Intrepid and have made a fun little emulation box with it.  (nes, snes etc etc)  Everything has been working perfectly for a few months now.  On 3/27/09 my update manager informed me that there were updates available so I let it run and everything installed correctly.  Before the update install everything was working fine (2 of the now broken programs Zsnes and Hedgewars, both worked perfectly minutes before update).  Now Hedgewars, Zsnes, Psx, and Gens refuse to even open.  I don't get any errors or anything, nothing happens.  I attempted to reinstall with no luck.  This is the list of updates from that day that I found in my history.  Does anything look like it could've caused the problem?

Commit Log for Fri Mar 27 22:03:45 2009


Upgraded the following packages:
cups (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-bsd (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-client (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-common (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
ghostscript (8.63.dfsg.1-0ubuntu6.2) to 8.63.dfsg.1-0ubuntu6.3
ghostscript-x (8.63.dfsg.1-0ubuntu6.2) to 8.63.dfsg.1-0ubuntu6.3
gnome-user-guide (2.24.0+svn20080922ubuntu1) to 2.24.0+svn20080922ubuntu2
libcups2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libcupsimage2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libgs8 (8.63.dfsg.1-0ubuntu6.2) to 8.63.dfsg.1-0ubuntu6.3
libicu38 (3.8.1-2) to 3.8.1-2ubuntu0.1
liblcms1 (1.16-10ubuntu0.1) to 1.16-10ubuntu0.2
xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1


I attempted to read the descriptions of all the updates but nothing stood out as affecting just these programs to me.  

Any help/ideas would be appreciated.  Thank you for your time.

---

### Post by Narclax on 2009-03-29
So far I have downgraded a few of the updates to see if the programs will start to work again with no avail.

So far i've downgraded these updates from above to their prior versions...

xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
libicu38 (3.8.1-2) to 3.8.1-2ubuntu0.1

I still cannot get any opengl (at least it seems its only programs using opengl) to open.

---

