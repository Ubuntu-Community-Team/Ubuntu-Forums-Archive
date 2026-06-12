---
title: "wd my book issues"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by hobojohn3 on 2007-12-17
i have a wd my book that worked for a while but now it doesnt want to work im very noob so pleas give details on questions of what to do i get an error when i try to mount saying it cant read superblock it hasnt been droped or bumped or anything when i plug it in it spins up then goes into standby mode please help

---

### Post by daviddehoog on 2007-12-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746Ze](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746Ze) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all

After a long, long time tracking this one down on IRC, we discovered that this was a replication of the following bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746Ze](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746Ze)
We applied the following workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/188](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/188)

But ... couldn't get blacklisting of ehci_hcd to work with /etc/modprobe.d/blacklist, instead we added only "modprobe -r ehci_hcd" to the /etc/rc.local file as a workaround for this kernel bug.

We also added "acpi=noirq irqpoll" to the /boot/grub/menu.lst boottime kernel options to workaround another USB-related kernel bug ! ([https://bugs.launchpad.net/debian/+source/linux-source-2.6.20/+bug/85488](https://bugs.launchpad.net/debian/+source/linux-source-2.6.20/+bug/85488))

Thereafter, the external HDD was recognised by Ubuntu and worked as hoped. Not easy, but certainly worth doing !

Cheers
Dave

---

