---
title: "Oracle-XE Apex problem on Jaunty Jackalope"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by wilkenw on 2009-05-04
I have been attempting to install Oracle-XE on "Jaunty Jackalope."  At the SQLPlus command line, all works properly.  I can backup/restore the database and perform normal SQL commands without any problem.  For what it's worth, I am running on a box with 2GB of RAM, a great deal free disk space, that is configured to support SMB networking and VMWare.

But ... Apex will not start on any port.  To eliminate the possibility of some wierd router problem, I disconnected my box from my network.  Problem persists.  To eliminate the possibility of some software issue with ports, I had the Oracle configuration program set up Apex on Localhost, port 80.  I have no problem pinging Localhost ... it is alive and well.  Also, I've made certain that all the recommended "tweaks" have been appended to my bashrc file.  

Similarly, I've installed Oracle-XE using both the Synaptic package manager and Debian download routes ... several times, with no different in results.  The only glitch I've observed in the process during one install was a broken.gvfs directory without ownership which I fixed with fsck.

Similarly, I've taken care to check all user and group memberships.  No apparent problems there.

This strikes me as something of a PATH or permissions problem.  Any ideas for a fix?

---

### Post by wilkenw on 2009-05-04
FINALLY! Problem solved!

THE problem resides in the Oracle listener file listener.ora.  Following a hint by another user frustrated with an inability to start the listener,
I commented out the following line in the listener.ora file:

(ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))

Apex now loads without a hitch.

What's not at all clear is why this "magic" really works.

---

