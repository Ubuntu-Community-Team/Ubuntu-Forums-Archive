---
title: "Catalyst 10.6 or default 10.4?"
date: 2010-07-03
forum: Hardware
---

### Post by sonnet on 2010-07-03
I have just installed ubuntu Lucid on my pc.
The restricted driver utility suggest me to install the closed ati proprietary driver which I believe are the 10.4.
-I know catalyst 10.6 are out. Which do you believe are better and specially stable for my radeon 4770?
-If I want install the 10.6 catalyst, how can I do that?

---

### Post by philinux on 2010-07-03
Just over a year old.

[http://ubuntuforums.org/showthread.php?p=7264005](http://ubuntuforums.org/showthread.php?p=7264005)

It might help. People seem to struggle with ati cards.

---

### Post by Yellow Pasque on 2010-07-03
Try the default Catalyst first. If 2D seems slow, try: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Slow_Maximizing_Windows.2FGeneral_2D_Slowness](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Slow_Maximizing_Windows.2FGeneral_2D_Slowness)

If that doesn't work well and you want to try 10-6, the directions are on the same link.

---

### Post by cutterjohn on 2010-07-12
Sorry for bumping an old thread, but catalyst 10.6 enabled their 2D acceleration scheme, which does help video playback somewhat...

AFAICS it's almost always best to go with the newest catalyst driver as they eventually fix bugs and sometimes improve(or decrease) performance.

Sometimes the buildpkg option is broken for Ubuntu, but you can usually find a fix on the phoronix forums in the ATI sub-forum.

I would use their binary installer... I mean the GUI one, seems best to go to the CLI and do sh ./ati-whatever-the-name-is.run --buildpkg Ubuntu/<whichever codename>

(the same command but with --listpkg will list all the packages that the scripts know how to build and IIRC give you an example command line to build a package...)

Then all you have to do is install the resulting .deb packages.  I usually just do: sudo dpkg -i *.deb

Might also want to/need to run aticonfig --initial (IIRC) which builds you a squeaky clean xorg.conf and backs up the old one to xorg.conf.fglrx-#  (if you have multiple monitors attach I think that you have to do --initial=dual-head, and --initial=check makes sure that the fglrx driver is being loaded/used according to the xorg.cong file, which should be good enough if you've made changes to your xorg.conf that you want to keep.)

I'm still on 9.10 ATM but am prepping to do a complete upgrade to 10.04 this time from scratch sometime today, tomorrow, or wednesday depending upon how things go... (want to get full benefits of ext4, and as a cheesey way of reclaiming disk space from unused apps and other cruft lying around... but I need to finish my backups first...)

---

### Post by luisg on 2010-07-13
In my case the default Catalyst proposed by Restricted Driver Manager has some power management problems, solved by Catalyst 10.5 and 10.6.

In return, I have to be very careful uninstalling Catalyst before applying any kernel or xorg updates, which is inconvenient and risky.

I wonder if Catalyst default Restricted Driver version will ever be updated by the Ubuntu team.

---

