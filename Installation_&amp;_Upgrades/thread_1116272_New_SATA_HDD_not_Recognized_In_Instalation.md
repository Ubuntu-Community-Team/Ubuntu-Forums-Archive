---
title: "New SATA HDD not Recognized In Instalation"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by a3uge on 2009-04-04
I have a XFX GeForce 8200 MPC socket AM2+ Motherboard with a AMD Athlon 64 X2 5800 CPU. The System was working with a IDE 120 GB HDD, but I wanted something a bit bigger so I bought a 1TB Seagate Barracuda HDD. I removed the existing drive and added the SATA drive.

When I went to install a Kubuntu 8.10 disk, it got to the partitioning section and didn't recognize anything. When I clicked next, it gave me an error that said "No root file system is defined. Please correct this from the partitioning menu." I went to the Live CD and checked for disks by using cfdisk. It gave me an error that said "FATAL ERROR: Cannot open disk drive."

I went to the BIOS and double checked that the SATA Drive was recognized there, and it was. I tried an Ubuntu 8.10 CD this time and had the same problem, and checked with GParted and it didn't recognize any drives.

At this point I'm stumped. I'm not sure if I bought a faulty drive or it's a problem with SATA and Ubuntu. Thank you for your help, and tips or information would be greatly appreciated.

---

### Post by ronparent on 2009-04-04
Lets see if the drive is alive>

From the live cd, what is the output of sudo sfdisk -l

---

### Post by tommcd on 2009-04-04
Try changing some of the sata options in the BIOS. See post #6 in this thread:
[http://www.linuxquestions.org/questions/linux-hardware-18/onboard-sata-drivers-for-xfx-geforce-8200-662850/](http://www.linuxquestions.org/questions/linux-hardware-18/onboard-sata-drivers-for-xfx-geforce-8200-662850/)
Also, when you boot the Kubuntu CD, hit F6 to add boot options and try **pci=nomsi** as it says in post #6. If that doesn't work try **all_generic_ide**.

---

### Post by ronparent on 2009-04-04
Right, bios may have to be activated in bios.

---

### Post by a3uge on 2009-04-04
Thanks tommcd,

The pci=nomsi did the trick. Can't believe I didn't see that before.

I'd buy you a beer if you were here.

---

### Post by tommcd on 2009-04-04
Glad it worked!
If you have problems booting after the install, you may need to add **pci=nomsi** to the kernel line for bootng Ubuntu in grub's menu.lst. See if you can boot it ok without it first though.

Oh, and welcome to the Ubuntu forums!

---

