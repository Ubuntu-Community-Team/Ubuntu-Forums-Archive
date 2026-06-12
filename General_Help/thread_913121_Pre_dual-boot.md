---
title: "Pre dual-boot ?"
date: 2008-09-07
forum: General Help
---

### Post by ManyBeers on 2008-09-07
I have a Sony Vaio PCGFXA47 laptop which currently is run by WindowsXP SP 3. And I am planning on installing Ubuntu 8.04 HH  in a dual-boot arrangement. My current setup looks like this:
RAM=512 mbs
Toshiba 20 gbs hd: 
C:\drive 6.5gbs Windowsxp(system)ntfs
D:\drive 7.8 gbs programs,and data(will be shared)ntfs.I will shrink this when installing Ubuntu
so there will be app. 5 gbs for Ununtu.
My system came with Recovery cds Not a WindowsXP install cd. This means there was no Recovery
Console included. Reading Aumha.org  Xp support forums one day there was a sticky that outlined the procedures neccessary to have the recovery console permanently installed on any XP computer
and have it available as a Boot.ini option. This is the link to the forum [http://aumha.net/]("http://aumha.net/"). Having done so my Boot.ini looks like this:
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
If I let Grub be the boot loader and install it into Windows mbr will it still offer Recovery Console as an option? I don't want to lose it. TIA

---

### Post by -Zeus- on 2008-09-07
it will almost certainly override the recovery console.

---

### Post by ManyBeers on 2008-09-07
> **-Zeus- said:**
> it will almost certainly override the recovery console.
So you are saying I will lose my ability to boot Recovery Console but will still be able to boot Windows?

---

### Post by -Zeus- on 2008-09-07
> **ManyBeers said:**
> So you are saying I will lose my ability to boot Recovery Console but will still be able to boot Windows?

yes.

---

