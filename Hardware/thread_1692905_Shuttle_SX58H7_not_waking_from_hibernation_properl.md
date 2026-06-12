---
title: "Shuttle SX58H7 not waking from hibernation properly"
date: 2011-02-22
forum: Hardware
---

### Post by hsivonen on 2011-02-22
I have a Shuttle SX58H7 computer (Intel X58 Express board, AMI BIOS version 08.00.16) with Intel Core i7 950 and GeForce GT 210 Silent (nvidia proprietary driver).

Under Karmic (64-bit), hibernation worked fine. Under Maverick, the computer goes to hibernation but when woken, USB and display don't come back and sshd doesn't respond, either. Sometimes when waking from basic sleep (as opposed to hibernation), sshd does come back and the computer can be reached from the network. IIRC, the regression happened when upgrading to Lucid.

Any ideas how to restore the hibernation capability that existed under Karmic?

---

### Post by hsivonen on 2011-02-22
Bug filed: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/723083](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/723083)

---

### Post by hsivonen on 2011-03-05
Solution in [http://ubuntuforums.org/showpost.php?p=9992908&postcount=33](http://ubuntuforums.org/showpost.php?p=9992908&postcount=33)

---

