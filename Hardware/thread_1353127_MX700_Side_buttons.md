---
title: "MX700 Side buttons"
date: 2009-12-12
forum: Hardware
---

### Post by Narusegawa on 2009-12-12
In 9.10 these work by default in applications like firefox, however nautilus doesn't like them.

The guides I've seen have all said to modify xorg.conf which as far as I know in 9.10 is generated automatically on boot and therefore now blank.

Well almost...

```
ection "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

How can I fix this? Nothing major it's just an annoyance really as I've gotten very used to having those buttons work in Windows Explorer the past several years and would like to continue the same in Ubuntu during my switch-over :)

---

