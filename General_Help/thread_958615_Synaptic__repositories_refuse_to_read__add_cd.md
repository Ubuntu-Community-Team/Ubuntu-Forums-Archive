---
title: "Synaptic / repositories refuse to read / add cd"
date: 2008-10-25
forum: General Help
---

### Post by slowtrain on 2008-10-25
Here's a tip that might be useful to anyone w/ the problem I just ran into (wasted a lot of my time).  I'm trying to install pptp.  When I use Synaptic, it asked me to insert my LiveCD, I insert it and click "OK" in the dialog box, and then it asks me to insert it again.  It's not 'seeing' the CD, even though I can perfectly well see the CD in Nautilus on my desktop.

Looking in /media, I noticed that the symbolic link cdrom points to cdrom0, but the LiveCD is mounted in /media not under cdrom0 but under its title.  So, I backed up the cdrom symbolic link (by renaming it) and added a symbolic link (ln -s) named cdrom that points to the disk name.  Now, suddenly, I can install pptp from LiveCD.  

Seems to me there is a bug in the way CD's are mounted, at least in relation to Synaptic's ability to use them.

Of course, now that i have them installed, there is apparently no working GUI for setting up the VPN.  A VPN option does not appear under the Network Configuration icon, as advertised.  May have something to do with my running Ubuntu 8.04 or having a 64 bit system.

Cheers!

---

