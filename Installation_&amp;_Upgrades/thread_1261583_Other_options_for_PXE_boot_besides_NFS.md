---
title: "Other options for PXE boot besides NFS?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by ziesemer on 2009-09-08
I'm working on getting the LiveCD available via Netboot within my LAN, as shown at [https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot) .

My question is: are there other options available besides NFS?  I can't find any documentation around the "netboot=nfs" option, or what exactly is even providing it.

I currently don't have an NFS server installed, but if it is the best option, that is the path I will continue with.  Otherwise, I was wondering if ftp, tftp, or smb would be some of the other available options - and what the advantages and disadvantages of each would be.  (Would any of these other protocols support streaming and/or random access of files, or would they all have performance penalties?)

Thanks!

---

### Post by ziesemer on 2009-11-06
While working on [something else]("http://ubuntuforums.org/showthread.php?t=1317317"), I found what provides the "netboot" option: [http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html](http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html)

---

