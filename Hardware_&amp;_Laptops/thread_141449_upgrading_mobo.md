---
title: "upgrading mobo"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by pixelnate on 2006-03-08
I am upgrading my mobo from a Shuttle AN-35 Ultra to an ECS Nforce3-A and was wondering if I will need to reinstall Ubuntu. It is a dual boot machine, and I have already resigned myself to a reinstall of Winders. But I have finally gotten Ubuntu _exactly_ as I want it, and would like not to have to start again from scratch. Setting up some of the apps was a major pain, i.e. Jahshaka and all the myriad multimedia codecs.

Can anybody give me some pointers on the upgrade? TIA.

---

### Post by glug101 on 2006-03-08
I don't think that you'll have to reinstall Ubuntu to make it work with the new motherboard, but I might be surprised.  Is the video card that you are using integrated in the motherboard?  If so, then you will likely need to start Ubuntu in text mode and run the x setup utility.  You also might need to reconfigure your sound if that was integrated also.

Hope the swap goes well:)

---

### Post by pixelnate on 2006-03-08
No, the video isn't integrated, but the sound is. Your post is encouraging. It semms like I will just need to reconfigure my sound. [sigh of relief] \\:D/

---

### Post by pixelnate on 2006-03-16
OK, I installed the new mobo, and have a small problem. While Grub loads properly and will take me to Windows without hassle, when I boot into Ubuntu I get an error something like "# bin/sh/ cannot find /dev/hdb1". Can anyone point me in the right direction on this one?

When I boot in recovery mode, I get all the vebose text where it spits up the same cannot find /dev/hdb1, but it gets past it just to tell me that it cannot find tty.

I have the haunting suspicion that it is a simple fix, but my kung fu is certainly not up to others on this forum and I am completely stumped.:confused: 

Any help would be greatly appreciated.

---

