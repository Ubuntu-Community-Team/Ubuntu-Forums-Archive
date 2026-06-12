---
title: "CD-ROM Drive Problems"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by ErikTheRed on 2006-02-08
So I'm trying to go from the 2.6.12-10 kernel to 2.6.15 w/ archck3.2 patch. Everything goes pretty smoothly except that my cd-rom drive does not want to work under the new kernel. I'm using an ASUS Z71v laptop. In the 2.6.12 kernel the drive shows up under kinfocenter as a SCSI device, if that makes a difference. I know my hard drive is actually SATA, so I guess it's possible the cd drive makes use of that same bus. To that end, I did compile the kernel with SCSI CD-ROM support, but it still fails to show up. Any help would be much appreciated here. If you need more data from me, lemme know.

---

