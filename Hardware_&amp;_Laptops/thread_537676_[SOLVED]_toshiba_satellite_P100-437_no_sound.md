---
title: "[SOLVED] toshiba satellite P100-437 no sound"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by kavatzoulas on 2007-08-29
hello from  italy
i am a new user of the wonderfull world of linux and i tried to install ubuntu.7.04 feisty fawn
my new laptop is a toshiba satellite P100-437 with cpu t7400 and Nvidia 7900gs 512m.
i ve made the install (i have a dual boot )everything working but NO SOUND  at all.
i tried almost the major part of the posts in the forum but still no sound.
the lspci gave me this. i have made the bios upgrade to 3.80


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

somebody to help?????
thank you

---

### Post by ddrichardson on 2007-08-29
Have you tried this [wiki howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28intel%29") - if so where do you get stuck?

---

### Post by vicgreek on 2007-08-29
I have the P100-437 and the only way I've found to get sound is to boot with acpi=off 
Try it.

---

### Post by kavatzoulas on 2007-08-29
the solution you gave me is working many thanks (&#963;&#949; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#969; &#960;&#959;&#955;&#965;)


sudo kate  /boot/grub/menu.lst
 find the line # defoptions  and change it to # defoptions=acpi=off
or if it is # defoptions=quiet splash change it to # defoptions=quiet splash acpi=off
save it
sudo update-grub

thats it 

many thanks for the help

---

### Post by ddrichardson on 2007-08-29
Glad vicgreek's suggestion worked - can you mark the thread as solved - it helps others looking for similar solutions.

---

### Post by kadir.ceran@gmail.com on 2007-12-01
my toshiba p100-437 baby is speaking for the first time :) 

thank you very much

---

### Post by kbzauy on 2007-12-05
OMG !!
this solved my sound problem !!!
many many thank you ! after 6 month of trying different settings, finally my computer speaks !!


now, is it much to ask for a tip on how to enable acpi and still have sound ??
without acpi my notebook does not turn off automatically, and it shows like it's always pluged in, so i don't know the battery remaining...


anyway, thank you again..

---

### Post by psepsas on 2007-12-08
Hi all i have exact this problem and i 've done those you told,
I am working on Ubuntu 7.10 release . I can hear only when i plug strong headphones and extremely low.I 've done many suggestions from this forum,like:[http://ubuntuforums.org/showthread.p...t=solved+sound](http://ubuntuforums.org/showthread.p...t=solved+sound)
[http://ubuntuforums.org/showthread.p...=ad1981+solved](http://ubuntuforums.org/showthread.p...=ad1981+solved)
[http://ubuntuforums.org/showthread.p...ghlight=ad1981](http://ubuntuforums.org/showthread.p...ghlight=ad1981)
and many other.
Now i have installed the newest available alsa drivers
and i have added those lines to /etc/modprobe.d/alsa-base
options snd-hda-intel model=toshiba
options snd-hda-intel position_fix=1 model=toshiba
options snd-hda-intel model=3stack
This is my my lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Thanks a lot
psepsas

---

### Post by octesian on 2007-12-30
I wouldn't consider this issue solved.  Its a known bug in that can be fixed in feisty but not in gutsy.

I'm not sure if this is the same how-to that I used but it looks about the same.  I hope it helps you as much as it did me.

[http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt]("http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt")

---

### Post by Mechanimal on 2008-03-16
Turning acpi off worked excellent, and will be a temporary solution until 8.04 comes out with more convenient fixes.

---

