---
title: "mobile integrated graphics controller not recognized on a toshiba a135-s4407"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by marcelocr2 on 2007-05-11
hi:

i have a toshiba laptop and i have installed ubuntu 6.06 lts, but the device manager shows that the mobile integrated graphics driver wasnt recognized...

my question is how could i install the drivers i need to solve this problem
the laptop is a toshiba a135-s4407
• Intel® Pentium® dual-core processor T2060
        o 1.60GHz, 1MB L2, 533MHz FSB
• Chipset
        o Mobile Intel® 943GML Express Chipset
intel media graphics accelerator for 950 dinamically allocated

thank you

---

### Post by benanzo on 2007-05-12
first I would say to update your PCI bus IDs.

```
sudo update-pciids
```

then do:
```
lspci | grep Display
```
or
```
lspci | grep Graphics
```

to see the exact chip you're using

---

### Post by marcelocr2 on 2007-05-13
thank you benanzo
 i did as you said and here is what the terminal shows me

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

now what i have to do???
thank you again

---

