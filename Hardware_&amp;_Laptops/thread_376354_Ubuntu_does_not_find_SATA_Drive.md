---
title: "Ubuntu does not find SATA Drive"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by emcneto on 2007-03-04
Hello,

After searching for a solution on the internet and multiple tries and installs I decided to write here.

I just installed Ubuntu 6.10 in my machine, and Ubuntu was unable to "see" the SATA drive. Here is a little history on the problem and the system.

CPU: Intel Pentium 4 (3.0 GHz)
RAM: 512 MB
Video Card: ATI All-in-wonder 9600 (128 MB)
HD: Primary - Seagate SATA 80 GB, Secondary - Seagate IDE 10GB
Motherboard: MSI 865PE Neo2-P

Windows is installed in the SATA drive and the IDE I use to install Linux. I am upgrading to Ubuntu from FC4, which worked perfectly with all my hardware, including mounting the SATA drive. When I had FC4 I had GRUB on the MBR of the SATA, for dual boot.

When I installed Ubuntu 6.10, the installation did not "see" the SATA drive, but I installed the system anyways in the IDE drive and placed GRUB in the MBR of that disk, just so I can boot into it (in order to do that, I need to change the boot sequence). I booted Ubuntu hoping that I would be able to see the SATA (Windows) drive, but no success. I looked around the web but did not find a solution. Can someone help me? I just need to be able to mount the SATA drive into Linux (I am aware that I will need to install ntfs-3g and all that). Here is the output of the "fdisk -l" command:

Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1190     9558643+  83  Linux
/dev/sda2            1191        1245      441787+   5  Extended
/dev/sda5            1191        1245      441756   82  Linux swap / Solaris

Just for the information, I also tried installing FC6 and Ubuntu Feisty Fawn Herd 5, but both give me the same problem.

Thank you in advance for the assistance.

Regards,
Eduardo

---

### Post by emcneto on 2007-04-09
Issue resolved...

I plugged the SATA in a different port, instead of SATA1 the windows HD is on the SATA2. No changes were required in the BIOS after that.

Eduardo

---

