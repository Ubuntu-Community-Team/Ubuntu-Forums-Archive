---
title: "Switching from FreeBSD (maybe)"
date: 2008-06-18
forum: Hardware
---

### Post by lil_elvis2000 on 2008-06-18
Hello,
  I'm having plenty of issues with my RAID 1 on my system. I'm running freeBSD on it. BUt when I copy or manipulate the large files on the mirror - the mirror falls apart (the drives disconnect) and it can occaisionally cause a panic (a crash). This can happen even when reading the files over a NFS mount, so not just a write issue at all.
  My hardware is Celeron 800Mhz, 640MB RAM, MB don't know, 1X11Gig IDE drive (the OS drive / /usr swap), 2X320GB SATA drives, PCI 3COM NIC, PCI ATI video, PCI SiL 3512.
  I'm waiting for the FreeBSD developers to get back to me on my problems. Looks to me like a problem with the meta writes with my configuration. Don't know if its a hardware issue. Have to check all connectors and cards and slots when I get time.

Anyone with similar hardware have any RAID issue with Linux. Which file system should one use. I see that there is XFS, maybe ZFS in the future and ext3.

---

