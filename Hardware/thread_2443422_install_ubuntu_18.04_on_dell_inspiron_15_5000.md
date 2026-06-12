---
title: "install ubuntu 18.04 on dell inspiron 15 5000?"
date: 2020-05-15
forum: Hardware
---

### Post by mikki2 on 2020-05-15
I have a Dell inspiron 15 5000 that came with windows on it.
I'd like to wipe and load ubuntu 18.04. The ubuntu lists says
this platform will support the OS. Has anyone had experience
wiping windows and reloading?
I ask because I've had problems and at this point, the BIOS
wont see the attached DVD or a USB configured as a startup.
I reset the BIOS to factory default. Based on other postings,
I also turned off secure boot. Under devices, I see RST but
I can't disable this. It's a single disk anyway (500G SSD)

What BIOS changes need to be made st I can (re)-try installing
 from DVD? 

Thanks
Mikki

---

### Post by oldfred on 2020-05-15
Best to backup Windows first.
Many later find one application or game they must have and it only works in Windows. Or want to sell system and have to have Windows installed.

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Dell is similar across many models, bigger difference if AMD or Intel.
Dell 5500 
[https://ubuntuforums.org/showthread.php?t=2436198](https://ubuntuforums.org/showthread.php?t=2436198)
 Dell Inspiron 5491
[https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes](https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes)
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
 Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

General UEFI install info in link in my signature, below.

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

