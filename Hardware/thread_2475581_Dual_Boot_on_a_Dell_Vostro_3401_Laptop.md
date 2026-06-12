---
title: "Dual Boot on a Dell Vostro 3401 Laptop"
date: 2022-06-01
forum: Hardware
---

### Post by astangl on 2022-06-01
I have a Dell Vostro 3401 notebook, with Windows 11 installed on the SSD and with Intel® Optane™ memory. I tried to install dual boot with the installation flash drive, but when I tried to install, the Ubuntu system asked to disable RST.


I was only able to solve the problem by adding an HDD and installing Ubuntu on it. But unfortunately I have to reset the bios every time I want to switch systems. Ubuntu only works if I change operating mode from SATA to AHCI and Windows only runs with RAID enabled. Also, I have to change boot sequence.


Does anyone know if there is a better way to solve this problem?
I tried to find another solution on the internet, but I couldn't find it.

---

### Post by sudodus on 2022-06-01
In a Dell Latitude 3520 Windows is installed with RST, and I could install Ubuntu 22.04 LTS alongside it without changing any setting in the UEFI/BIOS system. In a BIOS menu it is described as RAID on with VMD controller which can be managed by Linux kernel VMD driver (available in 22.04).

So I think it should be possible for you too. (I updated the BIOS while running Windows. It is now version 1.17.4)

---

### Post by oldfred on 2022-06-01
Lots of settings:
Dell Vostro 3500 i3-1115G4 Needs newest Ubuntu version & settings
[https://ubuntuforums.org/showthread.php?t=2465052](https://ubuntuforums.org/showthread.php?t=2465052)

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3593 Minor issues with fixes
[https://ubuntuforums.org/showthread.php?t=2448590](https://ubuntuforums.org/showthread.php?t=2448590)
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735) & 
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)
Dell app
removal (setuprst.exe and setupoptanememory.exe - both from Dell

---

### Post by astangl on 2022-06-03
ok i will check this, my bios version is 1.13.0. Thanks!


> **sudodus said:**
> In a Dell Latitude 3520 Windows is installed with RST, and I could install Ubuntu 22.04 LTS alongside it without changing any setting in the UEFI/BIOS system. In a BIOS menu it is described as RAID on with VMD controller which can be managed by Linux kernel VMD driver (available in 22.04).

So I think it should be possible for you too. (I updated the BIOS while running Windows. It is now version 1.17.4)

---

### Post by astangl on 2022-06-03
Thank you very much, I will study the options you indicated. If it works I'll let you know here.

> **oldfred said:**
> Lots of settings:
Dell Vostro 3500 i3-1115G4 Needs newest Ubuntu version & settings
[https://ubuntuforums.org/showthread.php?t=2465052](https://ubuntuforums.org/showthread.php?t=2465052)

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3593 Minor issues with fixes
[https://ubuntuforums.org/showthread.php?t=2448590](https://ubuntuforums.org/showthread.php?t=2448590)
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735) & 
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)
Dell app
removal (setuprst.exe and setupoptanememory.exe - both from Dell

---

