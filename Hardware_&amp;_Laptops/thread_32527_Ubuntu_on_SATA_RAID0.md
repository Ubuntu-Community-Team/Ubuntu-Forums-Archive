---
title: "Ubuntu on SATA RAID0"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by Vanye on 2005-05-08
Hello there!

I have a machine running a SATA RAID0 on a onborad Intel 82801ER SATA-RAID Controller (Asus P4P800 Deluxe Board).

That RAID contains the only disks on my computer, so I have to boot from there.
Currently I have XP SP1 installed, but I would like to change to Linux, and Ubuntu seemed a goot choice to me. :-)

Does anyone know if Ubuntu will boot and run on a hardware RAID?
I could not find any hint in the FAQs, and some posters in this forum seem to have troubles with RAIDS.

Second question: Is it possible to parallel install XP and Ubuntu on my RAID?

Thanks for help.


P.S. - this is my first posting on a forum and english is not my native language ;-) so please forgive me any mistakes.

---

### Post by poofyhairguy on 2005-05-08
[QUOTE=Vanye]

Does anyone know if Ubuntu will boot and run on a hardware RAID?
I could not find any hint in the FAQs, and some posters in this forum seem to have troubles with RAIDS.[/QUOTE]

Maybe. My software RAID works well...

[QUOTE=Vanye]Second question: Is it possible to parallel install XP and Ubuntu on my RAID?
[/QUOTE]

Maybe. If Windows is installed first.

One fo those things where you have to try and maybe fail to find out....

---

### Post by djgardyn on 2005-05-09
Great help poofyhairguy:

Explicity is the aim of newbies.

By the way...:
 	
Quote:
Originally Posted by Vanye

Does anyone know if Ubuntu will boot and run on a *[COLOR=Red]hardware RAID[/COLOR]* ?
I could not find any hint in the FAQs, and some posters in this forum seem to have troubles with RAIDS.


Maybe. My *[COLOR=Red]software[/COLOR]* RAID works well...

Okay, but what about the HARD way?  ](*,)

---

### Post by heimo on 2005-05-10
[QUOTE=djgardyn]
Okay, but what about the HARD way?  ](*,)[/QUOTE]

Real hardware raid controller is pretty much invisible (EDIT: transparent is probably the correct word) to operating system - OS would see the raid array as a hard disk and there would most probably be no problems booting Linux unless it's unusual (ie. very large partition, ~ >2TB).

Unfortunately raid contollers on motherboards are not pure hardware controllers and thus require support from OS. What I've heard, it's easier to use pure software raid or pure hardware raid in Linux and forget about motherboard raids / cheap raid controllers.

This way you gain some advantages. Pure Linux software raid (search for software RAID HOWTO in Google or Linux Documentation project, tldp.org) is transferrable from system to other system. Of course pure hardware raid is too (as long as the contoller is same or compatible), but these semi-hardware RAIDS are more problematic. Most probably you need exactly same motherboard, maybe even same revision of BIOS. Awful.

Is it possible to boot from software raid 0? I don't know. From software raid 1 it is. From hardware raid, yes, it's possbile to boot.

Hopefully this clears at least something. I only have experience on hardware raids (3ware is a good manufacturer for these) and Windows software raids. I would avoid using RAID-0 for anything, unless you're completely sure that's best setup for your system (better sustained transfer rate, possibly worse I/O performance). (EDIT: For many, two separate disks is better setup than two disks in raid0, but of course YMMV).

For excellent information on raid, check FAQ on [http://www.storagereview.com/]("http://www.storagereview.com/")

---

