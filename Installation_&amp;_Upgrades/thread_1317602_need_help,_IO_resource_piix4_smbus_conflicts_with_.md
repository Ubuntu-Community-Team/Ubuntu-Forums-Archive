---
title: "need help, I/O resource piix4_smbus conflicts with ACPI region SM00"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ibz41 on 2009-11-06
Please help, I recently installed ubuntu 9.10 32 bit and I am having issues booting. I tried using basic install cdrom which I could not get to install properly. I then used alternate install cdrom and made it through full installation. The first time I tried to boot the computer the ubuntu symbol came up for a moment and then screen went blank. I rebooted, waited for ubuntu symbol to appear and hit esc. Then i saw a message at the top of the screen "**general error mounting filesystems. A maintenance shell will now be started. CONTROL-D will terminate this shell and re-try. ****root@ubuntu****~# [9.887464] ACPI: I/O resource piix4_smbus [0xb00=0xb07] conflicts with ACPI region SM00 [0xb00-0xb07]"**
 
details: this is a clean install on a compaq sr1730z desktop, 2.2ghz amd athlon64 x2, 1 gig ram

---

### Post by wellilein on 2009-12-11
Same problem here.

Hardware: Athlon 2600+, 1 GB RAM
Server OS: Ubuntu 9.10 Server (minimum) 32 Bit + VMWare server 2.0.2
Guest OS: Ubuntu 9.10 Server 32 Bit with LAMP default installation

Problem occurs on guest OS at first reboot after installation.

---

### Post by guerilla on 2010-02-17
i have the same problem. trying to install 9.10 on my new machine.

AMD Athlon II X4, 4GB ram

---

### Post by mitack on 2010-04-02
Haha, for all the smarties out there who set their dates in the past to make vmware work after the trial expires:

The problem is that when ubuntu (THE GREATEST DISTRO EVER!!!) installs, it gets its date and time from the internet, and in a non-virtual environment, would set your computer's cmos clock correctly and it would be all good. In a Virtual Machine though, the VM cannot allow every guest OS to set the main time, so it disregards the change. And when the OS reboots, voila ! Your superblock had been mounted in the FUTURE !

So just go fsck yourself(pun intended), answer Y to the question to fix your last mount time and reboot and you will be OK !

---

