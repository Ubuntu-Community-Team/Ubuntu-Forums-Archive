---
title: "Reverting to Laptop Display"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by yzzir on 2006-08-25
Hello,

I have a Dell Inspiron XPS Gen 2 and I'm trying to get my external monitor(Samsung SyncMaster 730B) which is connected by the DVI port to work.  I inputted all the correct refresh rates and stuff but it still reverts to the laptop display when the GUI is loaded.  I'll post my xorg.conf when i get back home.  Any help would be appreciated.

Patrick

---

### Post by Woei on 2006-08-25
> **yzzir said:**
> I have a Dell Inspiron XPS Gen 2 and I'm trying to get my external monitor(Samsung SyncMaster 730B) which is connected by the DVI port to work.  I inputted all the correct refresh rates and stuff but it still reverts to the laptop display when the GUI is loaded.  I'll post my xorg.conf when i get back home.  Any help would be appreciated.

Well, if it doesn't work, the premise that you entered all the correct options in your xorg.conf file is bound to be incorrect. ;) You haven't told us what videocard is in that laptop, as there's a difference between plain vanilla X.org drivers and the binary nVidia drivers which allow things like TwinView through proprietary extensions.

Anyway, I'm running a laptop with an i855 chip, and I too have an external monitor connected to the laptop. The relevant parts out of my xorg.conf file are this:

```

Section "ServerFlags"
        Option "DefaultServerLayout" "crt"
        Option "DontZap" "true"
        #Option "DefaultServerLayout" "both"
        #Option "Xinerama" "true"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        #Option          "MonitorLayout" "LFP,CRT"
        Option          "MonitorLayout" "LFP,CRT"
        #Option          "MonitorLayout" "CRT,LFP"
        BusID           "PCI:0:2:0"
        VideoRam        65536
        Option          "CacheLines" "1024"
        #Option          "UseFBDev"  "true"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "Philips 190C"
        #Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-76
EndSection

Section "ServerLayout"
#        Identifier      "Default Layout"
        Identifier      "lcd"
        Screen          0 "Default Screen"
        #Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "ServerLayout"
    Identifier  "crt"
    Screen      1 "Philips 190C"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    #Option      "AIGLX" "true"
EndSection

Section "ServerLayout"
    Identifier  "both"
    Screen      0 "Default Screen"
    Screen      1 "Philips 190C" rightof "Default Screen"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
EndSection

Section "ServerLayout"
    Identifier  "clone"
    Screen      0 "Default Screen".
    Screen      1 "Philips 190C"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    Option "Clone" "on"
EndSection
```

I hope my working configuration files can guide you in making the necessary adjustments to yours.

---

