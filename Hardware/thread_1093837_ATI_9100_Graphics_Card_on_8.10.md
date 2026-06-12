---
title: "ATI 9100 Graphics Card on 8.10"
date: 2009-03-12
forum: Hardware
---

### Post by ZakSmith on 2009-03-12
Hey all,

I just got my old laptop fixed, it's a four year old Compaq Presario R3000 (Intel). It had a broken power port and was out of commission for about a year and a half. It had 7.04 on it and I decided to upgrade it, now that it is fixed. The old 7.04 system had the graphics card working straight out of the box, but the new 8.10 is giving me problems and I need some advice. Here is my "lspci -nn | grep VGA": 
```

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
```

And my xorg.conf:
```

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
```


I tried following this guide ( [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ), but everything I tried just messed up my system. Any help would be appreciated. Thanks in advance.

---

### Post by jocko on 2009-03-12
> **ZakSmith said:**
> Hey all,

I just got my old laptop fixed, it's a four year old Compaq Presario R3000 (Intel). It had a broken power port and was out of commission for about a year and a half. It had 7.04 on it and I decided to upgrade it, now that it is fixed. The old 7.04 system had the graphics card working straight out of the box, but the new 8.10 is giving me problems and I need some advice. Here is my "lspci -nn | grep VGA": 
```

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
```And my xorg.conf:
```

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
```
I tried following this guide ( [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ), but everything I tried just messed up my system. Any help would be appreciated. Thanks in advance.

The "radeon" driver is the only one that supports your card.
Change:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection
```
To:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection
```
But if you have tried to install ati's proprietary fglrx driver (which does not support your card), you need to get rid of every trace of it and reinstall some packages (don't remember exactly, but it could be "libgl1-mesa-dri" and "libgl1-mesa-glx").

---

### Post by ZakSmith on 2009-03-12
That did it, thank you very much.

---

