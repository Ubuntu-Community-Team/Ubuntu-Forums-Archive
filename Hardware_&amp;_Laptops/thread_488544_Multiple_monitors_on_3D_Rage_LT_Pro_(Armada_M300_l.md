---
title: "Multiple monitors on 3D Rage LT Pro (Armada M300 laptop)"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by paulhurleyuk on 2007-06-30
I have a Compaq Armada M300 ultra-portable laptop that I've installed Feisty 7.04 onto.  So far most things are working.  I'm trying to get the vga adaptor at the rear of the laptop setup differently from the laptop panel.  This works in Windows XP (<spit>) where I can have the two both working with different resolutions.

Everything I've found on the forum and google describes multiple monitors where two adaptors appear on the pci bus, but I don't have this...

lspci -v gives this info for the card;
```

00:05.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Unknown device b11b
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 3000 [size=256]
        Memory at 41080000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 28100000 [disabled] [size=128K]
        Capabilities: <access denied>

```

This is my current xorg.conf

```


Section "Device"
        Identifier      "ATI Technologies Inc 3D Rage LT Pro"
        Driver          "ati"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage LT Pro"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Anyone got multiple monitors working with a Rage LT Pro ???

Thanks

Paul.

--
[http://www.paulhurley.co.uk]("http://www.paulhurley.co.uk")

---

### Post by victorcache on 2007-11-04
I wish I had a solution for you but I think I have the same problem.   Not sure if you want to get the external monitor displaying something different than the laptop's LCD, or just want to get the external video display showing the same as the laptop's LCD.  I would just like to get the external video on, showing the same as the laptop's LCD.  Any help would be appreciated.  

I just recently installed 7.10 Xubuntu on my old Compaq Armada m300, after the Windows 98 installation got corrupted.

---

