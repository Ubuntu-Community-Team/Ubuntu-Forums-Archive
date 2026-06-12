---
title: "Nvidia hibernation black screen Lenovo p51"
date: 2021-04-12
forum: Hardware
---

### Post by 7a287120 on 2021-04-12
Hello,
 i have a problem with my p51 Thinkpad. Activating ubuntu from hibernation leads to a black screen. I tried to switch to nouveau (pk-client-error-quark : ..... ) or previous nvidia drivers (same problem). Is there a solution for this problem?

---

### Post by CelticWarrior on 2021-04-12
Welcome.

Please post the Nvidia model, drivers version and how did you installed it.

---

### Post by 7a287120 on 2021-04-12
Thank you. The Nvidia model is

```
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics P630 [8086:591d] (rev 04)
01:00.0 3D controller [0302]: NVIDIA Corporation GM206GLM [Quadro M2200 Mobile] [10de:1436] (rev a1)
```

the driver is nvidia driver 460. I did the ubuntu standard installation, no changes afterwards.

---

### Post by CelticWarrior on 2021-04-12
Driver version is correct for the Quadro M2200 Mobile. Hopefully you didn't made too much experiments without deleting the previous versions as that can create compatibility issues.

Now, you should update UEFI ("BIOS") before further troubleshooting.

And please explain exactly what you're using. Suspension or hibernation. The former is supported and should work fine with the proprietary driver. The latter ISN'T. Hibernation has been deemed problematic and was removed years ago from Ubuntu or Windows.

---

### Post by 7a287120 on 2021-04-13
I checked the current Bios Version

```
BIOS Information
        Vendor: LENOVO
        Version: N1UET80W (1.54 )
        Release Date: 11/05/2020
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 16 MB


```

Lenovo Bios update on Lenovo Page:


[LIST]
[*]BIOS Update Utility (Linux) 
[*]1.54 
[*]27 Nov 2020 
[*]5.52 MB 
[*]Critical 
[/LIST]

So Bios should be up to date? I had a dual boot system previous to this setup (ubuntu only). Bios was updated via Windows i think.

---

### Post by 7a287120 on 2021-04-27
The problem is no longer there. Dont know if the new updates solved the problem. Thank you for your help.

---

