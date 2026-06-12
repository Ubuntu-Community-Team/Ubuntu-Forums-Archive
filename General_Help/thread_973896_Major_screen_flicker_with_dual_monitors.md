---
title: "Major screen flicker with dual monitors"
date: 2008-11-07
forum: General Help
---

### Post by nandasunu on 2008-11-07
I just installed kubuntu-desktop 8.10 and with my dual monitor configuration the external monitor flicks on and off every few seconds making using KDE unbearable. I've searched for fixes with no success, any ideas?

I am using intel 945GM dual screen as a big desktop.

---

### Post by Peter09 on 2008-11-07
Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by nandasunu on 2008-11-07
> **Peter09 said:**
> Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

Here it is:
```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

---

### Post by Peter09 on 2008-11-07
You do not have the correct video drivers installed, as a first pass can you:-

Configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select xfix from the menu, this may resolve it. (Check 1. after doing this as well)

---

### Post by nandasunu on 2008-11-07
Thanks for your help. I've checked the hardware devices tool and I don't need any proprietory drivers (everything in the laptop has open source drivers available).

I rebooted and ran xfix but the flicker is still there in KDE4. Heres the output of lshw -C display again after running xfix (seems to be the same as before):

```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

---

### Post by nandasunu on 2008-11-07
So I did a bit more googling and found this bug: [https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/278471](https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/278471)

One solution in there was to disable the randr service, I did that and the flicker has gone :)

It seems that theres a bug in the intrepid KDE4 randr package.

---

