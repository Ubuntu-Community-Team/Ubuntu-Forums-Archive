---
title: "IBM IntelliStation Z Pro issues"
date: 2010-02-08
forum: Hardware
---

### Post by cronos6 on 2010-02-08
Hi,

  I'm trying to run Ubuntu 9.10 i386 on a 2005 IBM IntelliStation Z Pro 6221 22U with dual Xeon 2.8GHz HT, 3GB ECC RAM, 2 72GB SCSI drives and Quadro4 980 XGL.

  This PC worked PERFECTLY fine on Ubuntu 9.04. Since i've switch to 9.10, I can't use it anymore because it can't boot correctly anymore.

  I re-installed 9.10 i386 from a CD, everything went fine until the reboot. During the reboot, it looked on "Checking battery state". After a 120sec time out, Gnome shows up and I could log-on. I've updated my system include the new kernel and Nvidia drivers.

  From this time, I could not get the login screen anymore. By editing grub, I've booted without the "quiet" option, it boots, check hard drives, a bunch of lines appears, "AppArmor", etc.. and then, blank screen, ctrl+atl+F1 doesn't work, nor the Numlock key nor Ctrl+Alt+Suppr. I've waited 15min, nothing change.

  I've tried some options like "acpi=off" or "noapic" but nothing changed. I've also removed Nvidia drivers : still nothing.

  The OS boot correctly in "single" mode (aka rescue). I can login in cli without any problem.

  I've also updated the BIOS with a new one found on the [IBM website]("http://www-947.ibm.com/systems/support/supportsite.wss/selectproduct?familyind=5050008&typeind=5110912&modelind=5111078&osind=5166089&brandind=5000004&oldbrand=5000004&oldfamily=5050008&oldtype=5110912&taskind=2&matrix=Y&psid=dm"). 

  I've also change the BIOS battery to a new one : still nothing...


  Is anyone have a clue? Should I report a bug? I've attached logs I though it could help.

---

### Post by cronos6 on 2010-02-08
more documents

---

### Post by cronos6 on 2010-02-10
I up this post because I can't use anymore my PC :-/

---

### Post by cronos6 on 2010-02-14
Bug posted here : [https://bugs.launchpad.net/ubuntu/+bug/521879](https://bugs.launchpad.net/ubuntu/+bug/521879)

:-/

---

