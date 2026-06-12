---
title: "[SOLVED] SATA not detected"
date: 2008-10-21
forum: Hardware
---

### Post by RoyalPro on 2008-10-21
I have an ASUS P5Q SE.  I have Ubuntu running on the PATA channel off of the old hard drive of an upgrade that I am doing.  I got a SATA Lite-On DVD/CD burner and a SATA Seagate ST3640323AS 640GB hard drive.  I have both of them in the system and the BIOS sees them both.  When in Ubuntu I don't see the DVD drive or the hard drive.  I can't boot from the Ubuntu live disk it drops me to a busy box. I have the HDD on SATA(1) and the DVD on SATA(2).
Any one have any ideas?
Going to try a Gparted boot disk here in a few.

---

### Post by TuxPrincess on 2008-10-21
To be honest I'm a little confused with your post.

> "When in Ubuntu I don't see the DVD drive or the hard drive. I can't boot from the Ubuntu disk it drops me to a busy box. I have the HDD on SATA(1) and the DVD on SATA(2).

Ubuntu disk as in when you try to boot from the live cd or the hdd which would conflict with the previous sentence "when in ubuntu I don't see the dvd drive".

I would recommend booting from the gparted boot disk and ensuring the disks are formatted, also do you have any other operating systems which can access these disks with no problems?

Also for further help could I request which version of ubuntu you are using and your machine specification as this may help me and others (most likely others) to determine what is going wrong and how to fix it!

---

### Post by RoyalPro on 2008-10-21
Gparted will not boot either.  I am running 8.04 off the PATA drive.  I am going to burn a copy of 8.10 to see if that does anything better.

---

### Post by TuxPrincess on 2008-10-22
Does the disk you used to install 8.04 boot and if not have you checked that the cd-rom is given boot priority in your bios?

---

### Post by RoyalPro on 2008-10-22
After setting the BIOS to AHCI and not IDE for the SATA, I have got both the DVD drive and the hard drive working.  I can boot from the Ubuntu 8.04 CD, but not the Gparted CD.  I used 'dd' to copy my PATA hard drive to the SATA hard drive and it boots from the SATA hard drive now.
I love Ubuntu. If I would have done this upgrade with Windows I would have had to by a new copy of Windows.  So close to getting rid of Windows all together, if not for some games.

---

### Post by TuxPrincess on 2008-10-22
Good to hear you got it working in the end! :guitar:

---

### Post by RoyalPro on 2008-10-22
Thanks TuxPrincess

---

