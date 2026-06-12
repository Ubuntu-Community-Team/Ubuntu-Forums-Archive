---
title: "Install 5.10 ATI Rage Mobility M4 Drivers in 9.04"
date: 2009-10-21
forum: Hardware
---

### Post by rmsiegel on 2009-10-21
I'm trying to get full video support for my Dell Inspiron 8000 and its ATI  Rage Mobility M4 (AGP) video hardware. I've installed Ubuntu 9.04 and it does not seem to recognize the hardware at all. Here is the pertinent section of the xorg.conf file.

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

It seems to treating it as vanilla video hardware and it only runs at 800x600 instead of the fulll native 1400x1050 resolution.

I have a copy of Ubuntu 5.10 and running from the live CD it does properly recognize the hardware. Here it the 5.10 xorg.conf file:

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M4 (AGP)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage Mobility M4 (AGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

So the question is how can I get the video drivers from version 5.10 installed into version 9.04? Or is there another way to attack this? I have not been able to find other Linux drivers for the Rage Mobility M4 online.

Thanks in advance,
Bob

---

### Post by markbuntu on 2009-10-21
I think you would be needing the open source ati or radeon driver for that card but you should check the wiki first to make sure it is supported

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

