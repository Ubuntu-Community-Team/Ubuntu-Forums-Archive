---
title: "Broadcom Wireless Card for a HP Pavilion dv6000"
date: 2008-09-09
forum: Hardware
---

### Post by Thomas.Kast on 2008-09-09
I installed the software that was presented to me using Ubuntu. I get to the point where it asks for the password and then i enter the password, and it acts as if its trying to connect, but the wireless doesnt connect in the end. Anyone know what i am doing wrong?

---

### Post by sergiom99 on 2008-09-09
hi, your laptop exact model and specs would be fine for a start.
please post the output of the lspci command, and we'll find out which soundcard do you have. Type
```
sudo lspci
``` in a console shell and paste the output.
Which Ubuntu are you using (version, 32/64 bits, etc)??
Cheers.

PS: PS: This thread would give all the info you need to install Ubuntu on a DV6000 series. Works like a charm with almost no knowledge needed.
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

---

### Post by Thomas.Kast on 2008-09-10
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by Thomas.Kast on 2008-09-10
32 bit btw. and i installed tht package that u posted...im bout to test it now.

---

### Post by Thomas.Kast on 2008-09-10
Didnt work...

---

### Post by Thomas.Kast on 2008-09-10
It worked!! All i needed to do was a comptuer restart! Thanks dude for all your help!

---

### Post by sergiom99 on 2008-09-10
glad it worked.
now bookmark that thread for future reference.
Dark_stang wrote it, kudos to him.

---

### Post by Crafty Kisses on 2008-09-10
Please mark the thread solved. :)

---

### Post by mj330 on 2008-10-10
hi would someone help me please. i have the same laptop, same configuration. The internet doesnt work for me at all, not even the wired connection.

---

### Post by sergiom99 on 2008-10-11
well follow up in your original post:
[http://ubuntuforums.org/showthread.php?t=932568](http://ubuntuforums.org/showthread.php?t=932568)

---

