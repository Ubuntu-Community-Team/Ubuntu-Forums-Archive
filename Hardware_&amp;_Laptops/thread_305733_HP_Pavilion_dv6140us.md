---
title: "HP Pavilion dv6140us"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by dmery on 2006-11-23
Hi,
I have a HP Pavilion dv6140us, 2 giga ram, dual core AMD Turion64 TL56, Sata HDD (120 giga), nvidia 128 ram, etc.
I want to install Edgy on it. Someone has some experience in this subject ? I read that I need to install Ubuntu grub in a especial way in order to preserve the "Guindows" start up. I will try to install i386 because I had some troubles (problems with some programs, drivers and pluggins for 32 bits) with a 64 Ubuntu Dapper installed on  HP Pavilion zv6015us AMD Athlon64, 3500.
If someone knows where can I get information about this kind of installation, please let me know, I would appreciatte it.
Thanks in advance
cheers,
dmery:D

---

### Post by dmery on 2006-11-24
any idea ?
thanks

---

### Post by dmery on 2006-11-24
any help ?
thanks in advance

---

### Post by carlos1 on 2006-11-24
What is it that you're looking for exactly?
It seems like you want a general tutorial about how to install Ubuntu - is that correct? 
If you're asking about installing 32-bit Ubuntu on your Turion box, you can go ahead and do that. I installed the 32-bit on an AMD Athlon 64 X2 and it works great, no difference from a normal install.

---

### Post by dmery on 2006-11-25
Thanks for your help,
It is ok I will install Ubuntu 32 bits.
What do you know about a different way to install the grub, installing Ubuntu startup from Windows init ?
The reason would be maintain some Windows-HP features.
Do you know something about this stuff ?
Thanks in advance
regards,
dmery

---

### Post by tedgent on 2006-12-04
Hello,
I have the same model laptop and have successfully installed:

- Ubuntu edgy eft
- Kubuntu edgy eft (live CD only)
- SuSE 10.1 (dropped because of sound problems and system hangs they run kernel 2.6.16.20smp and upgrading kernel to 2.17.10 results in loss of USB connectivity)
- Freespire (dropped bacause of no SMP and poor graphics performance)

You MUST set noacpi for any of the distributions to work
I am currently running Ubuntu edgy eft using the 64bit distribution. Not all features work as listed but first to avoid hanging you need to F6 and set noacpi. Reply or mail me if you need help on the set up.

What works:
- base system, both CPU's recognised
- sound Speakers ONLY, not the headphone or mic 
- USB ports
- On screen display sound control
- hardline ethernet

What does not work:
- sound from headphone jacks
- camera (I have done no work on this, don't need it)
- Broadcom WIFI (I have done no work on this but there are posts on getting it to work)

What needs adjusting:
- display, defaults to 1068x768, need to change xorg.conf. I'll post my settings if anyone is interested. If you leave the display at default you will have font alias problems and poor graphics performance.

Instability:
- System runs glitch free except on return from screen saver when video goes into a reverse video mode. Reloading gdm solves that problem (logout and back in again) until the next sceen saver...

You can run the unix test crashme on this kernel and the system will run error and hang free!

best regards ted

---

