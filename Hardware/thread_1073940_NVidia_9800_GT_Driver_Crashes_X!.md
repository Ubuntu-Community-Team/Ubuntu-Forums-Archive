---
title: "NVidia 9800 GT Driver Crashes X!"
date: 2009-02-18
forum: Hardware
---

### Post by gradysghost on 2009-02-18
Just built a new system.  Specs:

AMD Phenom II X4 @ 2.9 GHz/core
4 GB DDR2-1200 RAM
2x 500 GB Western Digital SATA HDDs
2x BFG-branded NVidia 9800 GT video cards in SLI via cable

Installed Windows 64-bit.  That worked fine.  Went to install Ubuntu 8.10 x64 (my primary OS), and the install worked fine as well (done in 15 minutes flat).

Then went to install the NVidia propretary driver (v. 177).  Rebooted.  X won't start.

Things I've tried to fix this:

 - Manually install the NVidia divers (v 180.29)
 - Installed the 180 driver via Synaptic
 - Installed the 180 driver via Synaptic after adding the Jaunty sources (just to see if the beta for the next version would work)
 - Tried using envyng to install the drivers

In all cases, X will not start after a reboot.  GDM will start, only X will not.  I ran startx at the terminal and redirected the error output, which is pasted here:

```

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ryan-ubie 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 18 14:48:47 2009
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

Nothing is working!  Can anybody offer any ideas?  I've scoured these boards and have found that nobody has reported this identical issue!

---

### Post by gradysghost on 2009-02-18
Is anybody using an NVidia 9800 GT board in Ubuntu?  I can't be the only one...

---

### Post by Tahoe916 on 2009-02-18
Good luck finding answers here, not many people here to help with Video problems it seems as I have a similar question out there. Google digging time.

---

### Post by gradysghost on 2009-02-21
For anybody that comes across this thread with the same problem...  Read the second post on this thread:  [http://ubuntuforums.org/showthread.php?t=1056531]("http://ubuntuforums.org/showthread.php?t=1056531")

I haven't tested this yet, but it seems to have worked for everybody else, and it seems fairly straightforward.  Hopefully this works, and hopefully my linking it will keep people from searching for answers for three days the way I have.

---

### Post by gradysghost on 2009-05-03
For anybody still following this, my problem is solved only by removing one of the video cards.  The driver does not yet support SLI on these cards.  The list of supported cards only contains one SLI configuration, and it's on a pretty weak card by comparison.  So tough luck, but I like my Linux more than I like my video games.  Besides, one of these suckers is pretty damn fast.

---

### Post by izizzle on 2009-05-03
I had the same exact problem with my 8600GT

The Solution: Download the Nvidia 180.51 drivers from Nvidia's site and install them manually. They work like a charm, and I belive they support SLI as well.

---

