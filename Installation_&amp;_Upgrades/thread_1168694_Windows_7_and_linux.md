---
title: "Windows 7 and linux?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by f.diaz-maroto on 2009-05-24
):PJust wondering if anyone else who was dual booting Windows and Ubuntu updated to windows 7 without having to uninstall everything and reinstalling it again.

I think a how-to or a quick guide would be pretty useful for many people, not just me.:razz:

on a side note, what does the Ubuntu community think about windows 7 as opposed to vista and xp?
(i know i know, no one likes microsoft, but im curious to try out as many operating softwares as i can)

---

### Post by StormRoBoT2 on 2009-05-24
> **f.diaz-maroto said:**
> ):PJust wondering if anyone else who was dual booting Windows and Ubuntu updated to windows 7 without having to uninstall everything and reinstalling it again.

I think a how-to or a quick guide would be pretty useful for many people, not just me.:razz:

on a side note, what does the Ubuntu community think about windows 7 as opposed to vista and xp?
(i know i know, no one likes microsoft, but im curious to try out as many operating softwares as i can)

im using vista and ubuntu using grub work fine for me

ps: this is UBUNTU discussion board not WINDOWS :(

---

### Post by albinootje on 2009-05-24
> **f.diaz-maroto said:**
>  on a side note, what does the Ubuntu community think about windows 7 as opposed to vista and xp?
(i know i know, no one likes microsoft, but im curious to try out as many operating softwares as i can)

A lot of people actually like Microsoft a lot.

And I suggest to try out : FreeBSD, DesktopBSD, PCBSD, BeOS-Max, Qnx, Haiku-OS, and OpenSolaris, to start with, if you're interested in trying out other OS-es.

---

### Post by RyanVanDiemen on 2009-05-24
Im dual  booting win7 and kubuntu but i reinstalled the system completely.but you Can choose the partition for win7 during install, then just boot live cd and reinstall grub. Havent used vista before but im really impressed by win7 comparing to winxp.

---

### Post by IeU on 2009-06-16
I want to install Ubuntu on my PC, where W7 is already installed . . .

Anything that i should be aware of ?

Or is it the same process while installing Ubuntu on a PC with Vista ?


edit,

Another question, if i have an Intel Q6600 (64bit CPU), should i download the 32bit or 64bit version ? ( [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2) )

Just asking, because the 64bit iso is labeled as AMD64, so i thought, it could just work with 64Bit AMD CPUs . . .

Am i wrong ?

---

### Post by coffeecat on 2009-06-16
> **IeU said:**
> I want to install Ubuntu on my PC, where W7 is already installed . . .

Anything that i should be aware of ?

Or is it the same process while installing Ubuntu on a PC with Vista ?

Yes, it should be the same process. One thing to beware of - an issue that started with Vista, but I'm sure carries through to W7. **Don't** resize your Vista/W7 partition with a Linux partitioner, such as Gparted in the Ubuntu live CD. Not unless you want to fiddle about getting Windows to boot up again. All is explained here:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

(See under 'Using Linux to resize') - which links to:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/) 

> **IeU said:**
> Another question, if i have an Intel Q6600 (64bit CPU), should i download the 32bit or 64bit version ? ( [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2) )

Just asking, because the 64bit iso is labeled as AMD64, so i thought, it could just work with 64Bit AMD CPUs . . .

Am i wrong ?

Your Intel 64-bit CPU should run the AMD64 version of Ubuntu just fine.

---

### Post by mk1w86 on 2009-06-16
> on a side note, what does the Ubuntu community think about windows 7 as opposed to vista and xp?

I have used Windows 7 beta and RC and am pleasantly surprised after the mess MS made with Vista.

> I want to install Ubuntu on my PC, where W7 is already installed . . .

Installing Ubuntu on a machine with Windows 7 installed is the same as XP, Vista or any other version of Windows,  the installer should automatically add the boot entry to grub.

> Another question, if i have an Intel Q6600 (64bit CPU), should i download the 32bit or 64bit version ? ( [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2) )

Just asking, because the 64bit iso is labeled as AMD64, so i thought, it could just work with 64Bit AMD CPUs . . .

Am i wrong ? 

Although the iso is labeled AMD64 it also works on 64bit Intel CPU's.

The main reason to use the 64bit version would be if you have more than 4GB of RAM because the 32bit system will not see more than 3.7GB.

---

### Post by IeU on 2009-06-16
Thank you very much for all the answers !!!

What worries me the most is that i have always had problems with Grub  not recognizing Windows, so i have to do it manually.

I will give it a shot !!!

**CPU Type**->                                          QuadCore Intel Core 2 Quad Q6600, 2400 MHz (9 x 267)
**Motherboard Name **->                                 Asus P5Q 
**Motherboard Chipset**->                               Intel Eaglelake P45
**System Memory**->                                     8192 MB  (DDR2-800 DDR2 SDRAM)
**Video Adapter**->                                     NVIDIA GeForce 8800 GT  (512 MB)
**Monitor**->                                           Samsung SyncMaster 245B/245BW (Digital)  [24" LCD]
**Monitor**->                                           Samsung SyncMaster 245B/245BW (Digital)  [24" LCD]
**Audio Adapter**->                                     Creative SB X-Fi XtremeGamer Sound Card
**Disk Drive**->                                        WDC WD1500AHFD-00RAR5 ATA Device  (150 GB, 10000 RPM, SATA)
**Disk Drive**->                                        ST31500341AS ATA Device  (1500 GB, 7200 RPM, SATA-II)
**Disk Drive**->                                        USB Flash Disk USB Device  (964 MB, USB)
**Disk Drive**->                                        Kingston DT HyperX USB Device  (7 GB, USB)

---

