---
title: "no sound or touchpad since upgrade to 9.1 on a sony vaio VGN-FS21"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-11-07
hello all

we upgraded to 9.1 on a japanese sony vaio which had no particular issues, but as many others, we've lost the touchpad and sound.
i've been reading up on other threads but can't seem to find something to fix both issues.
we're using xubuntu but with the gnome desktop.

here's the lspci

kayo@kayogoro:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayogoro:~$ 

also, is there an easy way to logon automatically ? there's this logon screen where you have to click a user and type the password which was previously disabled.

thanks in advance for your help without which we couldn't pull through

all the best

ben

---

### Post by bjaz on 2009-11-07
bump

i'd really like to know if this is fixable or if i should downgrade the install. It's my wife's computer and she has to have it functional for when i'm away

---

### Post by bjaz on 2009-11-16
gave it up and switched to Ubuntu.
which works fine, appart from the PCMCIA card : no wireless since.
it did work on xubuntu karmic...

[PCMCIA wireless adapter, worked fine on all previous versions, doesn"t on Karmic, help..]("http://ubuntuforums.org/showthread.php?t=1322717")

---

