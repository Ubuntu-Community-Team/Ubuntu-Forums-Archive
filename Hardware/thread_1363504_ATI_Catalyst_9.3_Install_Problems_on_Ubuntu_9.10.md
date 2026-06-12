---
title: "ATI Catalyst 9.3 Install Problems on Ubuntu 9.10"
date: 2009-12-24
forum: Hardware
---

### Post by lapointj on 2009-12-24
Has anyone had any success installing ATI Catalyst 9.3 (needed for legacy ATI Mobile Radeon 9800 card in my Dell Inspiron 9100 laptop) on Ubuntu 9.10 (Karmic Koala)? 

When I run the command:
./ati-driver-installer-9-3-x86.x86_64.run --listpkg

The latest Ubuntu package supported is 9.04.

Obviously, when I run the command:
./ati-driver-installer-9-3-x86.x86_64.run --install

I get the following error:

> 
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-16-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.eR6He9


Is there any workaround to installing the proprietary ATI drivers for my video card (so that I can have OpenGL 3D support) for Ubuntu 9.10?

Thanks in advance.

---

### Post by emmesp on 2009-12-25
I have the same problem on my laptop, i need to have 3d working for my legacy Radeon x1300.
i spent all afternoon looking for a solution all i found is that catalyst 9.3 is not supporter after Ubuntu 8.10, and try some useless hack from other forums, if anyone has a work around please help
Thanks

---

### Post by 6dof on 2009-12-25
I'm running in to a similar problem and found that there is a beta version of Catalyst 9.10 which may work.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA)

Unfortunately it doesn't help in my case since my card is rather old.

---

### Post by chooks on 2010-01-18
I am having the same issue (ATI Radeon X850).  According to the PDF, the 9.10 catalyst driver does not support these older cards and the catalyst 9.3 driver documentation also says that future versions of the catalyst driver will not support legacy hardware. Of course, that doesn't mean that maybe 9.10 won't work (depending on your definition of "work").  

I'll give the 9.10 a shot but am not hopefull.  

- chooks

---

### Post by chooks on 2010-01-18
> **chooks said:**
> 
I'll give the 9.10 a shot but am not hopefull.  

- chooks

Results: I used synaptics to download the xorg-driver-fglrx and fglrx-amdcccle packages which apparently are the catalyst 9.10 drivers.  On installation, aticonfig could not find a device and the ATI Catalyst admin program could not either. Might try downgrading to an earlier ubuntu version or XP next.

- chooks

---

### Post by ssri on 2010-01-20
Installing ATI Catalyst 9.3 in Karmic is never going to work unless you downgrade xserver to Intrepid's version (1.5.2) and downgrade the kernel to Jaunty's 2.6.28, thereby breaking alot of things in your karmic install.  You will have to stick with the opensource drivers in Karmic.  Any legacy ATI card will not with any versions of Catalyst after 9.3.  You can thank AMD/ATI for this.

---

