---
title: "Installing 9.04 on a Compaq Presario SR1602HM"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by SysKoll on 2009-10-10
Hi folks,

A friend asked me to install Ubuntu on his old desktop, a 2005 Compaq Presario SR1602HM. It took me a while to solve the problem.

A regular install resulted in USB and Ethernet ports not working. The Ethernet is a regular Realteck 8139, and the 8139too was correctly loaded, yet the Ethernet port remained dead.

To solve this, the machine needs to be booted with the noapic kernel option.

With an Ubuntu CD, boot on the CD, then:
[LIST]
[*]Select the language
[*] Hit F6 (options)
[*] Select noapic in the list
[/LIST]

The OS then boots normally, and when you install it, the noapic option is copied into the GRUB command line. With this option, the Ethernet port works.

Note: this only solves the Ethernet port issue. The USB ports remain dead under Linux. Still working on this one. Any idea?

---

### Post by SysKoll on 2009-10-11
SOLVED! I went to the Compaq web site and found that this model had a BIOS update available. The BIOS updater is a Windows-only executable, which is why I am glad I kept the original Window OS on a separate partition.

The BIOS upgrade solved the problem. My USB mouse now works fine under Ubuntu on this machine.

---

### Post by ackley on 2009-10-11
My wife has this machine & I had to do that for her's, too. Glad you found the solution. Google-fu ftw.

Also be sure to edit your title with [Solved] in the title now. :D

---

