---
title: "PCI-e scsi card adaptec 29329lpe not detected AMD64"
date: 2009-05-25
forum: Hardware
---

### Post by Polaris96 on 2009-05-25
Is anybody running an adaptec 29320LPE Ultra 320 scsi card successfully?

I have this installed with 2 seagate cheetah 15k HDDs and the system will not detect the hardware.  I am running an AMD Phenom 9500 / 4GB RAM / Asus MVP motherboard currently on Kubuntu Intrepid (want to update to Pearson's Kde3.5 Jaunty, but I want to use the SCSI hardware for /, /var, and /opt.

I have tried every way I know to make it work.  This is where I am, now:

1.  card plugged into PIC-E slot.  two LEDs lit, so there is power
2.  Adaptec ultra 320 internal cable connected and terminated properly
3.  drives assigned SCSI ids via jumper (0 and 1 are used.  card defaults to 7)
4.  Internal Scsi drives don't have terminators, so that isn't an issue
5.  Adaptec confirms LINUX support (of course, they only support Red Hat and SUSE)
6.  Downloaded and aliened the rpm for AMD64.  dpkg'd the deb, didnt get errors, but restart confirmed the module isn't present (they mentioned an /etc/modules.conf file which was never created.  also, lspci still returns nothing from adaptec and no new drives in /dev)
7.  downloaded the source code, but I can't Make it due to the absence of a configure script in the tarball.  The README has basically nothing in it about installation or configuration, it seems to be only a changelog and some basic terminal commands for the card.  There is a Makefile but it dumps out with:

make: *** No rule to make target `/aic7xxx_seq.h', needed by `/aic7xxx_core.o'.  Stop.

if you try to Make it.  I hope there's autoconf data hiding in here, somewhere, but I sure can't find it!

I KNOW some people have these cards working because there are ref.s to them in the forum elsewhere.  Can anyone help?

---

### Post by Polaris96 on 2009-05-25
Solved this problem by the spagetti method (throw everything at it and see what sticks)

I'm not sure if all motherboards work like this or just ASUS.  Here's how it wound up working:

My motherboard (ASUS M3A32MVP-wifi) has 4 PCIe slots.  2 are coloured blue and 2 are coloured black.  If you have a device plugged into any of the PCIe slots, you must plug the second PCIe device into a slot OF THE SAME COLOUR for the BIOS to see it.

I don't know why this is ... it seems ridiculous, but I can't deny it worked.  After the device was plugged, the Kernel read it, no problem (I STILL don't know what's up with the source tarball.  If adaptec replies to my support request, I'll post it)

---

