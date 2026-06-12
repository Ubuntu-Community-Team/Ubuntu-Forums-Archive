---
title: "installing openoffice 3.0"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Tyco on 2009-03-10
Hiya, I am running ubuntu 8.04, and found a guide to install openoffice 3.0, however ran into a snag. at basically the final point to install it, i use the commmand:

cd OOO300_m9_native_packed-1_en-US.9379/DEBS/

but, it says DEBS does not exist. As far as i can tell, everything has downloaded correctly, so I am not sure what is wrong.

Any help would be greatly appreciated.

---

### Post by Neo_The_User on 2009-03-10
Open up a terminal.

```

cd OOO300_m9_native_packed-1_en-US.9379
ls

```

If what you're looking for isn't in there, it's not in there.

Check my thread out. The topic is off but a person posts a link on how to get OpenOffice 3.0 in that thread.

[http://ubuntuforums.org/showthread.php?t=1080993](http://ubuntuforums.org/showthread.php?t=1080993) Good luck.

---

### Post by Tyco on 2009-03-10
alright, i'll give it a go, thanks.

any other issues, and i will shout!

---

### Post by Neo_The_User on 2009-03-10
I'll be here waiting for any problems you have. Take care and good luck. ;)

---

### Post by Tyco on 2009-03-18
hiya, back again. found out the initial problem (i.e. i was trying to install .deb and they were rpm do-dahs (sorry, vocab failing me atm)). anyway, now we have a new and fun problem.

having tried to install the stuff again, i received the following from the terminal:

error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_11-fcs.i586
	/bin/cat is needed by jre-1.6.0_11-fcs.i586
	/bin/cp is needed by jre-1.6.0_11-fcs.i586
	/bin/gawk is needed by jre-1.6.0_11-fcs.i586
	/bin/grep is needed by jre-1.6.0_11-fcs.i586
	/bin/ln is needed by jre-1.6.0_11-fcs.i586
	/bin/ls is needed by jre-1.6.0_11-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_11-fcs.i586
	/bin/mv is needed by jre-1.6.0_11-fcs.i586
	/bin/pwd is needed by jre-1.6.0_11-fcs.i586
	/bin/rm is needed by jre-1.6.0_11-fcs.i586
	/bin/sed is needed by jre-1.6.0_11-fcs.i586
	/bin/sort is needed by jre-1.6.0_11-fcs.i586
	/bin/touch is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_11-fcs.i586
	/bin/sh is needed by jre-1.6.0_11-fcs.i586
	libfreetype.so.6 is needed by ooobasis3.0-core04-3.0.1-9379.i586
	libgnomevfs-2.so.0 is needed by ooobasis3.0-gnome-integration-3.0.1-9379.i586
	libgconf-2.so.4 is needed by ooobasis3.0-gnome-integration-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-en-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-es-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-fr-3.0.1-9379.i586

erm.......help?
basically, what does it mean, and how do i finally sort it out and install openoffice 3.0 at last?

any responses guys are, as always, welcome.

---

### Post by gomadtroll on 2009-03-18
I am new to this thread so pardon if this is old news. To get Openoffice in Ubuntu I would suggest Ubuntu's own packages from :
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/). You can add it to your sources list and let the package manager do all the work.

greg

---

### Post by Tyco on 2009-03-18
now THAT sounds like a plan....:D

---

