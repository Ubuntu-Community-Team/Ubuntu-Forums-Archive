---
title: "[Lucid] Problem with SeaGate 750GB HDD (Karmic works fine)"
date: 2010-05-29
forum: Hardware
---

### Post by Sintharas on 2010-05-29
Hi,
    I encountered a somewhat strange problem after switching from 9.10 to 10.04 (reinstall, no upgrade):

    Lucid has some problems with the 750GB-HDD of my hard disks (currently installed: SeaGate Barracuda 7200.11 500GB, 750GB; 7200.12 1000GB), but the other two are working without any problems. (Under Win7, all three are working without problems).
  Lucid hangs while shutting down sometimes, if apt-get updates grub, the updating process hangs till I killed the process and manually repaired grub after 40mins of inactivity(the HDD-Led was active all the time, and the system was really slow), if I try to mount one of the 750GB-HDD's partitions, the system slows down, but nothing happens, and after some time, i receive a error telling me that the Partition couldn’t be mounted, and that I should run chkdisk under win7.
  I did that, but chkdisk didn't report any problems.
  For updating grub and shutting down properly, I removed the SATA-Cable from the HDD, but this is not an acceptable solution as I need the Space and the files for my everyday work, and I don't really want to buy another HDD because under Windows and Karmic, everything is/was fine.

    How can I get details about the problems lucid encounters? I need to find out what exactly causes the problem. Should I backup the Data and remove all Partitions? Low-level-format perhaps?

    Thanks for your replies,
  Sintharas

---

