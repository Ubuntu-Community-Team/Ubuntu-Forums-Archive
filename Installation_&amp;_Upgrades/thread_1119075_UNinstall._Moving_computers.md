---
title: "UNinstall. Moving computers"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by HMCafe on 2009-04-07
dont worry I love Kubuntu i'm just moving it to a different computer. But i am giving my old computer to someone and i partitioned the drive when i installed it. so anyone know how to uninstall kubuntu and get the rest of the drive back for windows

---

### Post by upchucky on 2009-04-07
use gparted bootable cd to delete the partition, and then either create a new NTFS partition for windows to use as a storage partition, or grow the existing windows partition to fill the drive. then use the windows install disk utility called fixmbr to get windows to boot.

you should only do one partition step at a time.

---

### Post by RedSingularity on 2009-04-07
Yeah, gParted is the way to go.  Its very easy to use.

---

