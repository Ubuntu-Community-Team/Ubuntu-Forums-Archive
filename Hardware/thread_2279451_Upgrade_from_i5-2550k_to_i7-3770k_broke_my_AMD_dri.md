---
title: "Upgrade from i5-2550k to i7-3770k broke my AMD drivers"
date: 2015-05-23
forum: Hardware
---

### Post by ovimunt on 2015-05-23
Hi,

I'm on Ubuntu 14.04 LTS on a desktop PC with discrete AMD Radeon HD 7950 graphics card.

Until recently I used to have an i5-2550k CPU (no integrated graphics) with AMD proprietary drivers end everything worked just fine.

I then upgraded my CPU to i7-3770k (with HD 4000 graphics) and the AMD proprietary drivers stopped working straight away - the first time I tried to boot up it went into low resolution mode giving me some error about the graphics and stopped loading up. I've had to start in command line mode and manually remove all fglrx components to be able to start up.

I don't use the Intel graphics (my screen is plugged into the discrete graphics card) so I just want Ubuntu to ignore the Intel graphics and just use the AMD card. 

Could someone help me to get this sorted out please? Thanks in advance! :)

---

### Post by Vladlenin5000 on 2015-05-23
Can you disbale the integrated one in BIOS/UEFI?
If you can I think that would be a better (cleaner) solution.

---

### Post by ovimunt on 2015-05-23
I still need to use Intel QSV in Windows so I wouldn't really want to disable the Intel graphics in BIOS. In any case, it doesn't look like it can be done anyway.

---

### Post by Bashing-om on 2015-05-23
ovimunt;' Hello;

If you can not comply with Vladlenin5000's conditional;
You may find this tutorial of interest:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ovimunt on 2015-05-23
> **Bashing-om said:**
> ovimunt;' Hello;

If you can not comply with Vladlenin5000's conditional;
You may find this tutorial of interest:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Hey, thanks! I tried the Intel/AMD hybrid method and it worked!

---

### Post by Vladlenin5000 on 2015-05-23
Excellent news :p
Sorry if I couldn't be more helpful. You were at much better hands though.

---

### Post by Bashing-om on 2015-05-23
> **Vladlenin5000 said:**
> Excellent news :p
Sorry if I couldn't be more helpful. You were at much better hands though.

No way Hose !

I watch and learn so from you.

[INDENT][INDENT]I be "GrassHopper"
[/INDENT][/INDENT]

---

