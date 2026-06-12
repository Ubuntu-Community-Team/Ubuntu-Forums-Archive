---
title: "two hard disk controllers - disks not detected"
date: 2014-04-07
forum: Hardware
---

### Post by max40 on 2014-04-07
I have an old machine lying around which I installed Ubuntu 12.04.4 LTS on.
 I installed the OS to a USB flash drive.
 
The mainboard has an onboard ICH5 SATA Controller with two SATA ports. I plugged an additional SATA card with a JMB363 controller with two extra SATA ports into a PCI Express expansion slot.
 I want to connect three hard disks to the machine (independent non-raid).
 Both controllers seem to be detected correctly by Ubuntu.

  When I connect 1 or 2 hard disks to the ICH5 only, they are detected correctly.
 As soon I connect 1 or 2 hard disks to the JMB363, they are detected correctly, but any hard disk connected to the ICH5 is not detected any more.
 So in any configuration I tried I see a maximum of only 2 drives.
 I use "lshw -c storage -c disk" to find out which hd is detected by which controller.
Both controllers show up in the list no matter how many hard disks are connected and how.

  Do you have an idea how to make all three hard disks work?
 Thank you very much.

---

### Post by tgalati4 on 2014-04-07
Check the BIOS.  If you have IDE/SATA mode then you might only be allowed 2 SATA devices.  In SATA only mode you should be able to connect 6 or more SATA devices.  You would have to research your motherboard chipset for specific limitations.

---

### Post by max40 on 2014-04-10
Thank you for your comment [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895").
I finally solved the mystery: It was a hardware defect. The JMB controller somehow screwed it up.
I got a replacement card from the vendor and now I see all three harddisks as expected.

---

