---
title: "Ubuntu Server IDE/SATA problem"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by devastator on 2009-01-07
Hey Guys,

yesterday I downloaded Ubuntu Server to replace unRAID (Slack-based). In my BIOS I've set the SATA drives to AHCI mode, and the primary boot device to my IDE drive. The IDE drive is the primary master.

When I boot the installation disk, it lists 3 devices (correct) being /dev/sda (SATA), /dev/sdb (SATA) and /dev/sdc (the IDE one).
I want to install ubuntu on the IDE drive, as the 2 SATA drives will be used to create a RAID 1 array later on. When I want to partition the disk manually, the installer also lists a drive /dev/**h**dc with a capacity of 100 kb ???

Anyways, installing it on /dev/sdc (sdc1: swap, sdc2: / and sdc2 IS bootable) the installation succeeds. Whenever I'm asked to reboot however, ubuntu doesn't boot up. On booting It hangs after displaying "Booting from DVD ..." (no disc inserted). My previous Slackware install worked flawlesly in the same machine with the same drive setup ...

Any thoughts on this ?


Greets,
Deva

---

### Post by devastator on 2009-01-07
Nobody ?

---

