---
title: "Kingston memory showing up as &quot;Samsung&quot;?!"
date: 2014-09-12
forum: Hardware
---

### Post by maxbb on 2014-09-12
I bought a brand-new and sealed Kingston 16GB memory stick from NewEgg. However, when I run

```
sudo dmidecode --type 17

```
it shows

```
SMBIOS 2.7 present.


Handle 0x0043, DMI type 17, 34 bytes
Memory Device
        Array Handle: 0x0041
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 16384 MB
        Form Factor: DIMM
        Set: None
        Locator: P1-DIMMA1
        Bank Locator: P0_Node0_Channel0_Dimm0
        Type: DDR3
        Type Detail: Registered (Buffered)
        Speed: 1600 MHz
        Manufacturer: Samsung
...


```

There's only one memory stick in the machine, currently, so there is no possibility of confusing the DIMMs.

Is "Kingston" Samsung's brand? (An Internet search suggests "no") Is dmidecode wrong? Or did the manufacturer screw up?

---

### Post by gifford on 2014-09-12
Kingston will use Samsung memory chips. (Samsung manufactures chips)

---

