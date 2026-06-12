---
title: "How to uninstall vmware in ubuntu 8.10"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by ignitedintelligence on 2009-06-07
Hi Guys,

I've installed vmware workstation version 6 in ubuntu 8.10. I've installed it such that the launcher for vmware appears in the tools. when I click the program launcher "VMware Workstation", the program starts but it stops without going to the vmware window. Is there any bug in this? wat should i do to correct this error. else please tell me a method to uninstall vmware. when I tried to run the vmware-uninstall.pl file, it said the tar file cannot be located in /usr/lib/vmware/locations... how to uninstall vmware now? please help

---

### Post by nitheesh86 on 2009-06-08
Try this
    
sudo vmware-uninstall.pl

---

### Post by mgt_90 on 2009-06-08
How did you install vmware? If it was a .deb file, you can just apt-get remove, aptitude remove, or take it out with Synaptic.

---

### Post by Xavi-avi on 2010-12-27
You can also try these two commands:

```

sudo vmware-installer -u vmware-player
sudo vmware-installer -u vmware-workstation

```

---

