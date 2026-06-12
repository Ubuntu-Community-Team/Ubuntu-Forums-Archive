---
title: "Jaunty install - no internet connection for updates"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by philtrim on 2009-05-08
I have two machines I am playing around with, I installed Jaunty (9.04) desktop on both.  Neither currently has an internet connection.  But are wired together, via a x-over cable, and I cang ping each from the other.

I assumed NFS (file sharing) would be available, by default.  I wanted to just mess around and share from machine A to B.  When I try to share, it pops up and asks me to install either Samba or NFS, when I check NFS, obviously it fails, because of no connection to internet.

I then tried to download and install the .deb package for nfs-common.  It errored out stating missing dependencies, portmap & rpcbind.  So then I located portmap.deb, and tried to install this, got error - conflicts with sysv-rc.  So, I am bummed...
don't know where to go from here?

I was just wanted to share/browse either computer...but are unable to without either an internet connection (to add the necessary packages) or the correct version of NFS and it's dependencies..

Any ideas how I can proceed?

Thanks. 

Phil

---

### Post by StuartN on 2009-05-08
> **philtrim said:**
> Any ideas how I can proceed?

Most people use Samba for file sharing because it is simpler to set up. You will need to download either the NFS or the Samba packages in order to share anything - the client components are already installed, but not the server components.

---

