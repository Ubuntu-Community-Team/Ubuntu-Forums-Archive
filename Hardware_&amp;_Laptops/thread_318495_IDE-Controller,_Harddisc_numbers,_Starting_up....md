---
title: "IDE-Controller, Harddisc numbers, Starting up..."
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by theonlyandy on 2006-12-14
Greetings, everyone.

I'm trying to set up Ubuntu 6.10 Server on my machine.

I got one harddisc where Ubuntu is installed on, this disc is attached to the mainboards-ide-controller. I call that disc "system-disc".

Two other harddiscs are attached to my PCI-IDE-Controller.

So, the problem is as follows:
After every restart, the harddisc-numbers are assigned different. For example, most times the system-disc is assigned as hd0, but when starting the Ubuntu-Settup, it is assigned as hd2.

So, consequently Grub sais "Error 15: File not Found" when trying to boot, because he tries to boot from hd2. When I change the line "root (hd2,0)" to "root (hd0,0), Grub goes on and sais "Starting up...", but that's it.

So, my System hangs with this message "Starting up...".

Does anybody know what to do?
Do I have to edit the line where "root=/dev/hde1" stands to something else?

Grateful for your answers,
 Andy

---

### Post by theonlyandy on 2006-12-14
Ok, the problem is solved =)

I got a new Mainboard where I can attach all five IDE devices =)

That did it.

---

