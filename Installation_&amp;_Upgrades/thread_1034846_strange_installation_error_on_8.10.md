---
title: "strange installation error on 8.10"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by clark333 on 2009-01-09
Hi, this problem is driving me round the bend:-

I'm trying to install 8.10 version.  I put in my copy of Ubuntu in the drive (md5 checked, iso burned slow) then reboot.  My PC picks up the cd - and proceeds to load the setup menu.  I choose english, choose the option to install - and then after about 10 mins with the orange progress bar going good, i get this black screen with a list of initialised services entitled "fsck", the last item is blue tooth and all the items have a status of "ok" next to them.  The installation pauses and im left looking at this screen.

Does anyone have any ideas before i tear my hair out (whats left of it!).

---

### Post by Pumalite on 2009-01-09
Post your specs. Maybe a bad burn. Maybe little memory. Maybe difficult graphics.
Can you boot the Live CD to the Desktop?

---

### Post by kranny on 2009-01-09
try booting with the option acpi=off...and as pumalite said ur specs would be of more help to solve the issue

---

### Post by clark333 on 2009-01-09
I've just tried to install Linux Mint and the exact same problem happened.  I was thinking it could be the bootskin and logon screen ammendment software that i've got installed (and using).  Atleast I can rule out a bad CD, as i've md5'd and burned slow - more than one copy of iso.  I've also tried a cover magazine dvd of ubuntu with same problem.  Here is my specs guys:-

Ram - 2 gig
CPU - Intel core 2 cpu, 6600 @ 2.40Ghz
Hard disk - 350 GB
Mobo - Asus P5G-MX

Cant see any probs with my spec?

Your help is much appreiciated.

---

### Post by Pumalite on 2009-01-09
Graphics?

---

### Post by clark333 on 2009-01-09
graphics is NVIDIA GeForce 7600GT

---

### Post by clark333 on 2009-01-09
Just tried it again with my boot screen modification software uninstalled but the same thing keeps happening.  Someone said for me to boot with the option acpi=off, i have no idea how to do this?  It is freezing on the installation remember.

---

### Post by Pumalite on 2009-01-09
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by clark333 on 2009-01-09
Ive read that link and im no further forward.  From what i can gather, i have to edit the linux kernal somehow to make the installation work.  This could be beyond my skill level :(

---

### Post by caljohnsmith on 2009-01-09
When you boot the Ubuntu CD, at the first main menu, how about pressing "F6"; that will give you the chance to type in "acpi=off" at the end of a long line of kernel parameters. Then try booting from the main menu, and let us know how it goes.

---

### Post by clark333 on 2009-01-09
Hi again -

Ok, i've tried that with the acpi=off at the end of the string of code but  it didnt resolve, it keeps stalling on a black screen with a list of services that have been initialised.  I've never tried Linux before, so was desperate to see what it was like :(

---

### Post by Pumalite on 2009-01-09
Here is a list of boot parameters that you can try; one at the time or in different combinations:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317 vga=788 vga=789 vga=791

---

