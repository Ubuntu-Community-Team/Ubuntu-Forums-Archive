---
title: "Installing without synaptic"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by wbest on 2009-06-17
So, I'm at work and need to get some files on my Linux machine. I have the only Linux machine on the floor, and the network won't let me download stuff off synaptic.
 
The admins have a connection to the outside world at their station, but say they don't like me connecting to it for some reason, I assume security of the network or some bull...
 
Anyway, they said what they can do for me is put the packages on a drive and then have me put those files onto my Linux machine for installation. They plan to get it directly off the internet from direct links to te files, I think I've found them all.
 
Anyway, now that I have the setup under control, I can ask the real question:
Will I screw up my machine doing this? I mean, does synaptic serve more of a purpose than just making installing packages and such very easy? I'm not worried about viruses or anything, I'm just worried about painting myself into a corner by installing an incorrect of bad package.

---

### Post by 123456789123456789123456 on 2009-06-17
if the package is .deb, you can use the installer program to install it, it performs the dame actions as synaptic, for checking dependencies and the such.  That is the real reason why most use synaptic, it automatically checks compatability, with other packages that may be needed, and allous you to remove, add them to the que, in order to install programs.  It should not effect the machine, if you have to manually decompress and configure it, you run into dependency issues, of packages you need to find and configure in order to install/configure the packages you want.

---

### Post by wbest on 2009-06-18
Cool, thanks.
I'm still waiting for the IT people to get the files to me, so lets hope it all goes throguh okay.

---

### Post by MyR on 2009-06-18
to install multiple packages you can use sudo dpkg -i *.deb

peace

---

### Post by sgosnell on 2009-06-18
Synaptic is just another GUI frontend for dpkg.  You can use it to install packages from a disk by selecting File/Add Downloaded Packages, then navigating via the popup to the package you want to install.  Or you can use gdebi, another GUI frontend for dpkg, or you can use dpkg from the command line.  The end result is the same, it's just different ways of getting there.

---

