---
title: "Display Problem on Compaq CQ-50 Laptop"
date: 2008-09-13
forum: Hardware
---

### Post by landsg on 2008-09-13
Just bought a new Compaq CQ-50 laptop, and installed Ubuntu 8.04 (dual boot  with Vista).  This laptop has an Nvidia graphics chip in it, so I installed the Nvidia drivers via Envy, which seemed to work. 

However, when I open Firefox and scroll down a page, there are missing/garbled lines.  The resolution is 1280 x 800.  Here is an output after using the " lspci | grep -i nvidia" command:

00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0845 (rev a2)00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0845 (rev a2)


So, something is obviously very wrong with the driver install procesideas are s with Envy.   Thanks in advance for any help.

---

### Post by DoctorMO on 2008-09-14
why would you use envy instead of the Hardware Drivers program?

---

### Post by landsg on 2008-09-14
Sorry, I should have mentioned that I tried the proprietary drivers, but when I reboot Ubuntu goes into low resolution mode.  After that, I did some searching on the forums and found that others had used Envy with some success.  It does work better (no lo-res mode), but now I have the issue of the missing characters/lines.

---

