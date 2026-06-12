---
title: "Malfunctioning system or Ubuntu related?"
date: 2008-10-29
forum: Hardware
---

### Post by erisholm on 2008-10-29
Recently I had an attack on my Ubuntu Samba server, which required me to reboot. The problem is that it didn't make back to the OS. It passes BIOS fine every time, and makes it to GRUB, but the screen go blank immediately after and there is no disk I/O. This also happens when I try to boot from a rescue cd (Ubuntu Desktop and Ubuntu Server 8.0.4.1)

Strangely, boot failure is not always the case, as I have made it all the way to login two out of nearly twenty times. The first time after letting the computer be off for a couple of days, the other time after changing the cpu voltage setting. I tried to reboot the system both times, resulting in the boot problem mentioned above.

The computer is an old Asus A7M266 with a AMD Thunderbird 1400 Mhz (underclocked by pinstrip connectors to 1 Ghz) cpu, both from the year 2000. I ran a memory test showing no problems, and the hard drives (3x) should be fine.

I have no idea what the problem could be, and hope someone can provide some help or suggestions.

---

### Post by Coreigh on 2008-10-29
The fact that it will not boot from disk or CD is te red flag for me that some hardware failed. I know it is that case that if hardware makes it past 90 days (laptops and hard disks not counting) that it is probably golden...

BUT things do break and wear out. Maybe its not the hardware but the power supply?

---

### Post by Rocket2DMn on 2008-10-29
It seems that you have tweakead the hardware a bit, which if done incorrectly can cause damage in the long term.  Just because it has worked in the past, doesn't mean the system wasn't harmed - that and it's a fairly old machine.  Parts wear out, RAM goes bad, power supplies die, and hard disks kick the bucket.  Could be any combination of factors.
Also, passing BIOS doesn't mean something can't be wrong there, you may consider resetting defaults and even disconnecting unneeded hardware in case your power supply is strained or they are interfering with interrupts or on the bus.

It may be time for a new machine :)

---

### Post by JMorg on 2008-10-29
> **Rocket2DMn said:**
> It seems that you have tweakead the hardware a bit, which if done incorrectly can cause damage in the long term.  Just because it has worked in the past, doesn't mean the system wasn't harmed - that and it's a fairly old machine.  Parts wear out, RAM goes bad, power supplies die, and hard disks kick the bucket.  Could be any combination of factors.
Also, passing BIOS doesn't mean something can't be wrong there, you may consider resetting defaults and even disconnecting unneeded hardware in case your power supply is strained or they are interfering with interrupts or on the bus.

It may be time for a new machine :)

Aye, resetting the BIOS is a great start for this. If any tweaking has been done it can alter the way the pc is going to perform after BIOS loads. Just because a PC POST's (Power-On Self Test) doesn't necessarily mean you aren't having issues. If anything, reset the BIOS to defaults and edit the boot-priority to be CD-ROM first and try not only loading a live CD, but also try loading a bootable disc such as DFT (drive fitness test) and see if the different types of disc will load. But if none of this works then I also agree that it may be time for a new pc! :)

---

