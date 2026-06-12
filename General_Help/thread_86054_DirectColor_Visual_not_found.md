---
title: "DirectColor Visual not found"
date: 2005-11-04
forum: General Help
---

### Post by pickarooney on 2005-11-04
I'm trying to run a ftpish-type application called KDXClient.
It normally just requires that you unzip the package and run **KDXClient.lexe**, but when I do it I get the following error and the program fails to start:

```

 ./KDXClient.lexe
XWindows 24-bit DirectColor Visual not found!  Change display to 24-bit color.
KDXClient.lexe 9440: An unknown operating system error has occurred. (ID 1/27 @ W2028)

```

---

### Post by pickarooney on 2005-11-04
I can't get the hang of the gnome config utils, there seems to be no usable options in any of them... how do I change the display to 24-bit colour?

Is it by changing the 16 to 24 in the line bolded below in xorg.conf?

Section "Screen"
    Identifier "screen1"
    Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor "COMPAQ 7500"
    **DefaultColorDepth 16**
    Option    "TwinView" "True"
    Option    "TwinViewOrientation" "Clone"
    Option    "SecondMonitorHorizSync" "30-50"
    Option    "SecondMonitorVertRefresh" "60"
    Option    "MetaModes" "1024x768, 1024x768; 800x600, 800x600;"
    Option    "TVStandard" "PAL-B"
    Option    "TVOutFormat" "SVIDEO"
    Option    "ConnectedMonitor" "CRT, TV"
    Option    "TVOverScan" "0.4"
    Subsection "Display"
        Depth 8
        Virtual 1024 768
    EndSubsection

    Subsection "Display"
        Depth 15
        Virtual 1024 768
    EndSubsection

    Subsection "Display"
        Depth 16
        Virtual 1024 768
    EndSubsection

    Subsection "Display"
        Depth 24
        Virtual 1024 768
    EndSubsection
EndSection

---

