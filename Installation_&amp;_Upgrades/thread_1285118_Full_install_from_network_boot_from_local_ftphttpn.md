---
title: "Full install from network boot from local ftp/http/nfs available packages"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by glug101 on 2009-10-07
My appologies if this is answered elsewhere, but I keep finding similar methods, but not exactly what I am looking for.  I'm considering having an installation party for the release of Karmic, and thought it would be cool/efficient to install the OS over the network.  Since this installation method is certainly NOT available for windows, I feel it is a good example of some of the fundamental differences of Linux versus Mac or Windows.  Also, I can get away with burning a simple netboot loader and use the same cd with all the pcs.

So far, I have successfully setup netbooting through PXE and loaded a Ubuntu (9.04) install image.  The problem I have is that the image tries to pull all the packages over the internet.  This will NOT be cool during the early release period, since I don't want to eat bandwidth on the repositories if I don't have to, and I don't want to wait for EVERYTHING to be pulled from repositories.  

I must confess that it might be better to just burn a bunch of alternate install CDs and run the installs that way since I don't honestly believe that I'll get that many people to come to the install party, but it's an interesting exercise that I am very close to cracking.  

In short: I would like to know if anybody knows a way to get a network booted image to pull install files from a local server through FTP/HTTP/NFS.  

Thank you so much :)

---

### Post by ikisham on 2009-10-07
I don't know if I understand your question.
If you install from the mini.iso then you may only install the packages you want from the net.
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/)
The link above is for the current Karmic mini but if you browse backwards from it you'll find the beta one.

---

### Post by glug101 on 2009-10-07
> **ikisham said:**
> I don't know if I understand your question.
If you install from the mini.iso then you may only install the packages you want from the net.
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/)
The link above is for the current Karmic mini but if you browse backwards from it you'll find the beta one.

I'm looking for something very similar to the mini.iso, but I want to pull the packages from an http or ftp repository on my local intranet.  :)

Fortunately, I may have found the missing piece that I am looking for [here]("https://help.ubuntu.com/community/PXEInstallServer").  Looks like creating a Kickstart file allows  you to redirect the installer to pull packages from an http server of your choosing:)

Sweet!

---

