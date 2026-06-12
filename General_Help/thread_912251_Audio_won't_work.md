---
title: "Audio won't work"
date: 2008-09-06
forum: General Help
---

### Post by joefixingfrankscomp on 2008-09-06
Hi people and thanks in advance for your help.  My brother's computer pooped out so I used Ubuntu from CD to get all his data then I wiped the slate clean and installed Ubuntu instead of XP (like he had before).  When I installed Ubuntu on my computer a while ago everything worked perfectly immediately.  I've got everything working here except the audio isn't working on the computer.  Please help.  I can't figure out what kind of audio card it is except the computer is a Sony Vaio VGC-RC110G.

---

### Post by wolfen69 on 2008-09-06
do ```
lspci
``` to find out what you have for audio. post it here.

---

### Post by joefixingfrankscomp on 2008-09-06
Here it is.  Also, as an FYI, I left a small XP partition and the audio works fine...I don't know if that helps.  Much thanks!

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by cooke77 on 2008-09-06
If you have lefted a small XP partition.....suggest that you look at the AUDIO (in it's "Control Panel")...to see what it says.
That will give you a good idea of what the Sound card is.
Your details...are very suggestive that the Sound card is......Realtek. (The 'High Definition' bit.)
Change to a Creative Labs Sound card, you may have better luck...with your Sound.
(Creative are 'supportive'....of Linux OSs. Realtek is not.)
I have Realtek HD Audio (inbuilt)..on my computer.
Works fine with XP, does not..with Ubuntu 8.04 LTS/Kubuntu 8.04.
Swapped to Creative, not a problem since.

---

### Post by joefixingfrankscomp on 2008-09-06
Thanks.  I'm getting the impression this issue can't be fixed.  This is my brother's computer, so I'm not about to buy him an audio card.  Since, when my brother opens his wallet, you can hear an echo, I guarantee he's not going to buy it.  It looks like I'm going to have to switch his computer over to XP (the sound card won't work with Vista).  Thanks anyway guys.

---

