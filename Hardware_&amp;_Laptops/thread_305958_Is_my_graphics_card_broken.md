---
title: "Is my graphics card broken?"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by marteus on 2006-11-24
I am experiencing issues with my zepto znote 6214w with nvidia gf 7600 go card. It sometimes refuses to initialise. A reboot or two (or three) gets it working again. 
I dual boot with windows and so far I have not seen something like that (Though a week ago the system (windows xp) was performing misserable (though not like running on standard vga drivers) and I had to reboot to get the performance back, but thats not something soo strange i windows).

So my problem is that I really can't complain if I only have problems in windows (since the manufacturer doesn't support linux).
But if it is a hardware failure then I can send it to rma.


I've uploaded dmesg from when the system works and when it doesn't
It seems that it has something to do with irq 10

---

### Post by Sandriman on 2006-11-24
Are you using the official nvidia binary drivers, or the free X implementation, aka "nv" driver?

Umm, you could try appending:

pci=routeirq acpi=force pnpbios=off

to the kernel command line. Just a guess. I remember having similar problem some time, but can't remember what parameters I used to fix it. Try those if it works :)

---

### Post by marteus on 2006-11-24
The official proprietary one.

---

### Post by hardkaare on 2006-11-26
Hi im having problems with my zepto 6615wd go 7600!
when I use the official nvidia drivers, and make changes between consols and X ctrl+alt F1-7, a few times the machine hangs.
and the same thing even happens sometime when I reboot.

This dossent happens with nv(xorg drivers)

I have tryed with, with the nvidia drivers from packages system and the newest one, same result!

and I have tryed with the kernel parameters.

strange!

---

### Post by olia on 2006-11-27
Same problems here with zepto 6214W and nvidia go 7600. The nv drivers works fine, but not the nvidia. The computer hangs 8 of 10 times on reboot/shutdown and when changing between consoles. The nvidia driver worked fine under dapper drake so ill probably change back if I dont find a solution soon..

---

### Post by marteus on 2006-11-27
Hm then perhaps it is not broken (unless yours is broken too - though the bios has an option to specify OS (the different versions of windows and "Other")), which is both good and bad :???: 

It has never failed me 10 times though (at most 4-5 times in a row).

Wonder if it's kernel issues.

---

### Post by marteus on 2006-11-27
@olia is your dmesg like mine when the driver fails?

---

### Post by hardkaare on 2006-11-28
I have tryed cnages the os thing in bios to other, that dossent changes anything :-(

I made a bug report on nvidia's forum. hope they find a solution.

---

### Post by hardkaare on 2006-11-28
I have tryed changes the os thing in bios to other, that dossent changes anything :-(

I made a bug report on nvidia's forum. hope they find a solution.

---

### Post by hardkaare on 2006-11-28
I have tryed changes the os thing in bios to other, that dossent changes anything :-(

I made a bug report on nvidia's forum. hope they find a solution.
[http://www.nvnews.net/vbulletin/showthread.php?t=81256](http://www.nvnews.net/vbulletin/showthread.php?t=81256)

---

### Post by marteus on 2006-12-01
My issues has been solved here with bios update z115.. what a mess ](*,)

---

### Post by hardkaare on 2006-12-02
Lets hope Zepto comes up with a bios update that fix the problem for the other models too.

---

