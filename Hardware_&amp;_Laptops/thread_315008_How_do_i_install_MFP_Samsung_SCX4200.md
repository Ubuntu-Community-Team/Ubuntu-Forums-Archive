---
title: "How do i install MFP Samsung SCX4200??"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by krolyk on 2006-12-08
Hi to all!
I have a MFP Samsung SCX4200, and tried to install driver from original cd.
I have logged in as root and in terminal typed what was written in GUide:

[root@localhost root]#cd /media/cdrom0/Linux 
[root@localhost root]#./install.sh

and appears such an error:

-bash: ./install.sh: /bin/sh: bad interpreter : permission denied

Help please who have installed such a printer. ](*,)

---

### Post by le_mec on 2007-01-04
I had the same problem. Most probably the cdrom is mounted "noexec", I didn't check though.
This means you cannot run the script from the cd.

The easiest way is to copy the content of the cd to your hd. This should work (it did for me..)

---

### Post by geradamas on 2008-01-13
This is extremely difficult:

you have to use sudo -i

and then make sure you copy the Linux folder from the CD into the Home folder - doesn't work elsewhere.

Oddly enough copying from the install CD is a huge waste of time as you then have to set permissions on every file you copied.

I downloaded the driver package from Samsung and popped that in my home folder.


However; Samsung get a fairly offensive noise from me as "Linux compatible" is a bit disingenuous! The average "Plug-N-Play" customer will get cheesed-off before the 2 hours it took me.

---

