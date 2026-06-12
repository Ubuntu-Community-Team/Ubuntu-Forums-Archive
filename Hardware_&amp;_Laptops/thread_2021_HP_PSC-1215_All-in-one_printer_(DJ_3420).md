---
title: "HP PSC-1215 All-in-one printer (DJ 3420)"
date: 2004-10-25
forum: Hardware &amp; Laptops
---

### Post by Greg on 2004-10-25
(has same print engine as HP Deskjet 3420.)

Has anyone been able to print to this device? I have mine connected via a shared XP box on the Lan, and all that happens when printing is the paper loads and then after a brief pause, it unloads again, leaving a partially downloaded print job in the queue.

My other windows boxes print fine to this shared printer, but Ubuntu (or any Linux for that matter) won't talk to this printer in the way it wants. I have tried various other drivers in the HP range and also I have downloaded and installed the latest drivers from HP's Linux printing project with no joy.

Any ideas?

---

### Post by MNCaudill on 2004-10-29
I have the HP PSC-1210 all in one (probably basically the same printer). I printed a test page, and after that it worked. I know that's not a good fix, but it worked for me.

---

### Post by yotam on 2005-02-13
Any progress using this PSC1215 with Linux?

---

### Post by JoWilly on 2005-02-13
You guys should use the search function :)

The PSC 1215 works perfectly, I have installed one a few days ago.

1. install hpoj
2. reboot (if you do not reboot it will not work)
3. add new printer (1215 does not exist, driver for 1210 works perfect).
4. it works.

---

### Post by ubuntu UsER on 2005-05-12
[QUOTE=JoWilly]You guys should use the search function :)

The PSC 1215 works perfectly, I have installed one a few days ago.

1. install hpoj
2. reboot (if you do not reboot it will not work)
3. add new printer (1215 does not exist, driver for 1210 works perfect).
4. it works.[/QUOTE]

Hello, 
My problem is **there are no psc-series entries**, so i can't choose neither 1200 nor 1210 :| 
PS. I have no problems under KDE.

---

### Post by ubuntu UsER on 2005-05-12
[QUOTE=ubuntu UsER]Hello, 
My problem is **there are no psc-series entries**, so i can't choose neither 1200 nor 1210 :| 
PS. I have no problems under KDE.[/QUOTE]

*g* i noticed that i uninstalled by mistake packages which include printer drivers information, now everything works pefrect  :grin:

---

### Post by Philipude on 2005-06-17
Hi PSC users

If you like the scanner effect in addition to the printing I recomment [https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29)

Have fun

Phillip

---

### Post by DiGiTaLFX on 2005-07-22
Hi

Thanks for the guide to getting it working. That was really helpful. Anyway being a bit inquisitive I decided to go find out about hpoj and when I found the homepage it said for USB based printers HPLIP should be used instead. Should I remove hpoj and put on hplip? Seeing as its made by HP I presume it would be a better choice?

DiGiTaLFX

edit: I've just removed hpoj and was about to try and install hplip and i was told I had to remove ubuntu-desktop. Any ideas?!?!

---

### Post by Shiven on 2005-07-27
i just added how to set up hplip on ubuntu with scanning/printing funtion onto the wiki, on this page here: [https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29)

hope this helps!

---

### Post by tudortatar on 2005-09-01
[QUOTE=ubuntu UsER]*g* i noticed that i uninstalled by mistake packages which include printer drivers information, now everything works pefrect  :grin:[/QUOTE]

hi,
i seem to have the same problem here, **no 1210 driver** in the list. You said it was because you removed a package. What package is that? maybe it'll work for me too.

Thanx a lot.

---

