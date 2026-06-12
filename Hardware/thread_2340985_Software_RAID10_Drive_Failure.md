---
title: "Software RAID10 Drive Failure"
date: 2016-10-24
forum: Hardware
---

### Post by crlanglois on 2016-10-24
I have a system running Software RAID10 composed of 4 drives as the boot volume.  I was naive and assumed that if a disk failed I would still be able to boot with this setup however I cannot.  My system shows one drive (SATA2) has failed on boot "SMART Capable and Status BAD", the other 3 show status OK.  It then boots into grub rescue.  The drives show in grub but any attempts to look at them show "error: unknown filesystem", this makes sense as the raid itself isn't working.

Does anyone have any tips or helpful resources you can refer me to to recover to where I can boot from my raid and eventually replace the disk and rebuild?  I'm thinking it was a bad idea to boot my OS from a software raid however at this point I just want to recover using my 3 working disks.

Thanks for any tips ahead of time.

---

