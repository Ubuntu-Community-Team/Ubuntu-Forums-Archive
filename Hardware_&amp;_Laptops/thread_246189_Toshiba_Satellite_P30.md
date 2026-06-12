---
title: "Toshiba Satellite P30"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by EricJosepi on 2006-08-28
I realize that most people are running dell and HP on here so I hope that someone can save me!

I installed ubuntu back about year ago and decided that after the sound card ended up not working, I decided enough was enough and wiped it off my system.  I am now looking at a fresh reformat and dual booting ubuntu and Windows.  Does anyone know if this problem has been cleared up.

It runs Realtek AC97 audio according to my Windows Device manager.

Thanks,
Eric

---

### Post by lmp on 2006-09-03
Hi, I have a Toshiba Satellite 2180 CDT and I did have sound, but my mike did not seem to work.
I installed Xubuntu dapper drake (6). After installing skype for linux beta (incl QT compiled in it) the mike suddenly worked with skype. (not with the sound recorder).
So if you need this, use this.

Please be aware that dapper drake might have a wireless problem for the rt2500 driver. It drops the line ...

succes.

---

### Post by petermck on 2006-09-03
I have a new Satellite M50, which uses a ATI IXP SB400 AC97 sound card. Everything works fine and was easy to install, although the wifi only seems to work with WEP.
The only problem I've got is the power management seems a bit flaky. When I unplug from the mains it just hibernates.

---

### Post by sebastfr on 2006-09-04
hello... I have a Satellite A35 with AC97 and that works fine (out of the box)... I can even use it in parallel with my external sound card.

seb

---

### Post by gkellerman on 2006-11-30
Yes, I have tried Edgy Eft on a Toshiba P30 (Ubuntu).

The:
Sound card works perfectly
The network card work perfectly
After a bit of configuration the WiFi worked perfectly (nothing scary here)
I did not check the software modem but I don't think it worked?
The ATI 9700 was working fine.
The touch pad worked fine.

The ENE Technology card reader still does not work (did not work on ANY of the other distros I tried).  

HOWEVER:
Inserting a USB device not only functioned only at USB1.1 speed but also ruined some of my data when moving it from a USB drive to the laptop drive.  It would create 16Kb files only with what seemed to be random (there is no such thing as random in a computer) input/output errors.  I suspect this has to do with the Toshiba ACPI!  Suse is the only distribution that got this right out-of-the-box.  Fedora 5 and MEPIS (which is also a Debian/Ubunta variant) gave me the same issues.  You might want to disable ACPI to see whether this fixes the problem on Ubuntu but you are warned!

PS:  Toshiba support for Linux is non-existent.  Will not support Toshiba again if I want to run Linux on it.



The sound card works perfectly, the nextwork works perfect

---

