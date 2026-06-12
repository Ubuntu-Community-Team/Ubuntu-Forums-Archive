---
title: "Repeated entries in xinput (Video bus, power button)"
date: 2018-01-09
forum: Hardware
---

### Post by abh98 on 2018-01-09
OS : Ubuntu 16.04
System : Dell inspiron 3558 laptop

Following is the xinput output:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; DLL06B0:00 06CB:78F1                        id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                       id=15    [slave  keyboard (3)]

```

As you can see it shows two video bus and power button entries. How to fix this. I think this is messing up with my suspend sometimes as my laptop sometimes does not wake from suspend (Blank screen), but not always

I also have bumblebee installed.

uname -a :
```
Linux abh-Inspiron-3558 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Any help appreciated

---

