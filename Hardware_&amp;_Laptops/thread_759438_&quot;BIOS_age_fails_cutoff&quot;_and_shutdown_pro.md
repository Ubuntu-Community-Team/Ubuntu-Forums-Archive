---
title: "&quot;BIOS age fails cutoff&quot; and shutdown problems"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by panayk on 2008-04-19
Hi!

I just installed xubuntu on a rather old PC. The motherboard is Soyo 6vba-133.
During boot i get the message: "BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI", but the system boots normally. I tried adding the "acpi=force" option, but that triggers an instant reboot.

My problem is that shutdown does not finish normally, i.e. the computer does not power-off. What's more the power button does not work at this stage, so my only option is to pull the plug. And to make things worse, as soon as I reinsert the plug, the computer powers on automatically, without pressing the button.

I had this problem in Windows 2000 also, but not Win98.

Hopefully you can help me,
Many thanks!

---

### Post by fain on 2008-04-19
Try updateing the bios to the mother board.

---

### Post by philinux on 2008-04-19
I had this and adding acpi=force to the kernel options in grub solved it. Unless there was a kernel upgrade and it got wiped.

I manage to find an upgrade to the bios and it cured it permanently.

To be honest if everything works but you have to pull the big switch to power off it's not a big deal.

---

### Post by panayk on 2008-04-21
Thanks for your suggestions.

Between replacing a drained CMOS battery and fixing a faulty power supply, I got "acpi=force" to work and got rid of the "reboot after shutdown" problem.

The problem now is that with acpi enabled I have horribly jerky mouse movement. I hope the BIOS update will help.

I agree it's not much of a problem, but the person who will be using this computer is basically new to computers, so I didn't want to scare him off. Perhaps there is a way to display a "It's now safe to turn off your computer" kind of message?

---

