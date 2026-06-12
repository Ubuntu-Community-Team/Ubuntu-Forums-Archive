---
title: "partition editor problem"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by orestisz on 2009-10-26
[B][FONT=Arial]hi

i m completely new to ubuntu. I downloaded [/FONT][/B]**[B][FONT=Arial]Ubuntu 9.04 [/FONT]**[B][FONT=Arial]Desktop and created the cd, ran the file wubi.exe, chose *"demo and full installation" *and rebooted the system using the option *"help me reboot from cd"*.
Now the problem is that when i begin installation every time the partition editor begins to run (that would be step 4) the installer stops responding, so i can only run ubuntu thru the cd. what can i do to install ubuntu on my hard drive? [/FONT][/B]
[/B]

---

### Post by stlsaint on 2009-10-26
u want wubi or [dualboot]("http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu")?

---

### Post by orestisz on 2009-10-27
i m not sure i understand what you mean...
could you specify this a little?

---

### Post by Mark Phelps on 2009-10-29
Ubuntu can be installed in two very different ways in a system that already has an MS Windows OS -- to preserve that OS.

The first is done using Wubi and installs Ubuntu INSIDE MS Windows in a special file that Ubuntu treats as a partition.  The plus is that you don't have to deal with partitioning; the minuses are that (1) this is really designed to be a trial of Ubuntu, not a permanent solution and (2) if MS Windows crashes, since you use the MS Windows boot loader to select Ubuntu, you can lose access to Ubuntu as well.

The second is done by "shrinking" an existing partition to make room for the two Ubuntu partitions, creating those partitions, installing to those partitions, installing the GRUB boot loader, and booting into GRUB later to select which OS you want to run.  The plus is that Ubuntu is running in its own partitions and thus safe from MS Windows problems; the minus's are (1) if you have Vista running and use the Ubuntu installer to shrink the OS partition, you run the risk of corrupting the Vista OS, (2) you overwrite the MS Windows MBR such that, if you every have to repair the MS Windows install, it will wipe GRUB from the MBR and you'll have to install it again.

---

### Post by orestisz on 2009-11-11
i downloaded ubuntu 9.04, burnt the cd and rebooted from the cd. The installer automaticaly runs, and after being asked about the location i live in the partition editor intializes and then i get no response whatsoever.
I also tried to run wubi from within windows vista. It does run but when i click on istallation it runs the installation programme which stops responding again when the partition editor initializes, just after asking me what language i want to use (i tried choosing various languages too). 
Any suggestions?

---

