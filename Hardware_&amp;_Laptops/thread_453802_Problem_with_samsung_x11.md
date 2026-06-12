---
title: "Problem with samsung x11"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by Mullins on 2007-05-24
i am having some probelms installing any linux operating system on my samsung x11, i am new to all this so i shall apologize if i sound a bit dumb.

to start of with i have managed to instal ubuntu on a pc in the past however i seem to be unable to do it on my laptop. During the install it gets to about as far as loading acpi modules and then freezes with no system processing after.

if anyone could provide any ideas or solutions that could help me get passed this i would be very greatful

Regards
Mullins

---

### Post by Mullins on 2007-05-24
any chances of anyone bothering to read this

---

### Post by Shisoik on 2007-09-06
I have the same bug. If you pass "acpi=off" as a kernel parameter the system will boot up. Don't forget to add the same option to menu.lst file in /boot/grub and perform update-grub after installation.

---

### Post by Shisoik on 2007-09-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64308) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				BTW, this bug is already reported.

---

