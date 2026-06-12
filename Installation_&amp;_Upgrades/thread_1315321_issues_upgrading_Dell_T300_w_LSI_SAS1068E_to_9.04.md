---
title: "issues upgrading Dell T300 w/ LSI SAS1068E to 9.04"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2009-11-05
Hi,

I'm having issues upgrading my Dell PowerEdge T300 from 8.04 to 9.04 (via first upgrading to 8.10). basically the problem is that the kernels / initrd images in 8.10 and 9.04 don't recognize the LSI SAS1068E SATA RAID controller, and thus won't boot. interestingly, the kernel / initrd from 8.04 recognizes the controller fine.

I wonder if support has been removed from the newer kernels? or maybe we put it into the 8.04 manually and will have to do the same? (frankly, it was quite a while ago :)

are these controllers not supported by stock Ubuntu kernels?

the controller in quesiton is:

07:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)

---

### Post by nutznboltz on 2010-07-02
You are not alone.  See this bug report:

[https://bugs.launchpad.net/debian/+bug/474207](https://bugs.launchpad.net/debian/+bug/474207)

---

### Post by nutznboltz on 2010-07-02
Related thread

[http://ubuntuforums.org/showthread.php?t=933467](http://ubuntuforums.org/showthread.php?t=933467)

---

