---
title: "Jaunty freezing"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2009-06-21
I've just installed Jaunty & find it freezes completely (have to flick the power switch) from 10 seconds to a minute or so after booting, though a couple of times it's lasted an hour or so.  It makes no difference which applications are in use.  Changing the boot parameters to irqpoll pci=noacpi noapic nolapic acpi=off didn't help.  Nor did installing from the alternate install CD.  The first time it didn't freeze so soon I managed to update the kernel to 2.6.28-13 & install the proprietary nVidia drivers, but that didn't help either.  The PC's got an AMD Sempron300+ processor with 1.2GB RAM & an nVidia GeForce FX5500 graphics card.  Has anyone got any ideas about what I could try next ?

---

### Post by sdbrogan on 2009-06-22
All filesytems are ext3 by the way

---

### Post by wpshooter on 2009-06-22
Have you checked the integrity of your live & ALTERNATE Ubuntu CDs ?

---

### Post by sdbrogan on 2009-06-22
Yes, I checked the md5sums after downloading them & used the 'Check CD for defects' option before installing

---

### Post by masux594 on 2009-06-22
When does this problem start rising? After an update, ever, from a couple of days? As I understand maybe ever.. well, first of all.. How old is the pc? I had the same problem with a 5 years old notebook.. It runs Xp and sometimes it freeze for 10-30 seconds.. Changing the OS to Interpid, the problem persists..  I think is some problem with HW that cannot be resolved by an OS.. 

P.s. The freezing problem start from one day to the next! =| Sometimes happen, sometimes not..

Sysc, A

---

### Post by sdbrogan on 2009-06-22
The PC's a few years old, but it ran XP fine & then Intrepid - the problem appeared as soon as I installed Jaunty

---

### Post by masux594 on 2009-06-22
So this is a fresh installation.. Does it freeze when you start an application or another "ACTION", or it happens suddenly?

Sysc, A

---

### Post by Peulders on 2009-06-22
I'm having the same problem with jaunty. On start-up it freezes before login, if I install nvidia drivers then I get in a start-up loop where the pc instead of freezing just reboots over and over again. I have a GeForce 8600M GS. Currently the only thing that works is using vesa.

---

### Post by sdbrogan on 2009-06-22
It happens even if I don't launch any applications

---

### Post by sdbrogan on 2009-06-23
I think it might be to do with this bug : 355155.  There's no fix in view so I've gone back to Intrepid for the time being.

---

### Post by WA4MOE on 2009-06-27
I have the same problem after upgrading to Jaunty. My Toshiba Laptop is fine and has been running great with Intrepid. It was a download directly to the machine and upgraded. No CD involved.
Now I guess I may lose all my data and photos just to go back and  downgrade.

I love Ubuntu but this is frustrating. My desktop did upgrade to 9.04 with a couple of hitches but they have been resolved and it's working fine.

Help....

---

### Post by Peulders on 2009-07-23
> **Peulders said:**
> I'm having the same problem with jaunty. On start-up it freezes before login, if I install nvidia drivers then I get in a start-up loop where the pc instead of freezing just reboots over and over again. I have a GeForce 8600M GS. Currently the only thing that works is using vesa.

Since the update of kernel version 2.6.28-13 to 2.6.28-14 the problem seems resolved. No more freezing at startup or endless loops. So if you are experience freeze/scrambled screen at startup and installing nvidia drivers resolves in a loop you may want to upgrade your kernel version. Enjoying ubuntu with very nice 3D support, resolution of 1280x800,...

---

