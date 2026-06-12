---
title: "Sparc Ultra 30 Install"
date: 2008-07-28
forum: General Help
---

### Post by MW1LCR on 2008-07-28
Hi all

I have been given a Sun Sparc Ultra 30 workstation, complete with Tape Drive and **HUGE** monitor, having been used for CadCam in its previous life.

I now want to install Linux, preferably Ubuntu, on the workstation. Which version should I download and install ?

Thanks 

Adrian

---

### Post by Fire_Chief on 2008-07-28
You'll need to download Ubuntu 6.06 for SPARC and install it. This was the last version that supports the SPARC platform. Then you can do upgrades via APT to get the latest updates on the system.

On the download page from Ubuntu.com, there is a link at the bottom of the page for a full download list. Select a mirror close and then find the 6.06-SPARC ISO to download. It will be listed as a server version instead of desktop. Don't worry about that, you can still install all of the desktop stuff after the initial system installation.

Cheers!

---

### Post by miguel_lobos on 2008-07-30
> **Fire_Chief said:**
> You'll need to download Ubuntu 6.06 for SPARC and install it. This was the last version that supports the SPARC platform. Then you can do upgrades via APT to get the latest updates on the system.

On the download page from Ubuntu.com, there is a link at the bottom of the page for a full download list. Select a mirror close and then find the 6.06-SPARC ISO to download. It will be listed as a server version instead of desktop. Don't worry about that, you can still install all of the desktop stuff after the initial system installation.

Cheers!

I'm pretty sure there's a 7.04 or 7.10 release for SPARC, as I installed on an Ultra 5 with 7.04 from CD. The image is probably in a similar location, but I haven't looked to see if its still there. One thing I ran into with the Ultra 5 is even with the latest version of OpenBoot, I still had to set the boot device to the CD-ROM to get the CD to boot (i.e. at the OK prompt, type boot-device=cdrom, then reset-all to reboot).

On another note, the last 'official' release on SPARC is 7.10, but if you want to upgrade to the latest release, the SPARC platform has been moved over as a port. You'll need to update your apt configuration files to point to the right 'port' servers to upgrade beyond 7.10.

Hope this helps, and have fun on SPARC!

Lobos
:guitar:

---

### Post by miguel_lobos on 2008-07-30
Upon more research, you can download a Hardy Heron port ISO image here:
[http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04.1-server-sparc.iso]("http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04.1-server-sparc.iso")

Happy SPARCing!

Lobos

---

