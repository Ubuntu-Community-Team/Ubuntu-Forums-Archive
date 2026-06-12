---
title: "Installing Ubuntu on VMWARE 5.5"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by gavinb on 2006-02-09
This might be more of a VMWare question, but I was hoping someone here has done this.  I am trying to install Ubuntu on VMWare 5.5.  It copies all of the files to the virtual harddrive.  It gets stuck setting up the repositories.  I am thinking it has something to do with the ethernet setup, and ubuntu is unable to see the internet?  The computer is behind a linksys router.  What settings should I use for the ethernet.

Thanks
Gavin

PS
My real ubuntu pc works just fine behind the same router.

---

### Post by el3ktro on 2006-02-09
Which type of network setup do you have for VMware? There's bridged, NAT and a third one. You'll want "bridged networking".

Tom

---

### Post by gavinb on 2006-02-09
Thanks Tom,
I will give that a try.

Gavin

---

### Post by benco on 2006-02-09
If your network conf is correct and it still does not work, it might be a proxy issue. 
I installed Ubuntu yesterday in VMWare (from the Ubuntu VM available on VMTN) as a bridged guest and after tweaking the apt.conf file I can reach the repositories and update the distrib.

---

### Post by gavinb on 2006-02-09
Unfortunately that didn't work.  It is still hanging a 25%

---

### Post by jkwuc89 on 2006-02-09
I installed 5.10 into VMWare Workstation 5.5.1 using the ISO image as my CDROM.  I installed VMWare Tools after logging in for the first time.  With VMWare Tools, the networking will not work.  The directions in the downloadable VMWare User Guide contain the information necessary to install VMWare Tools.

---

