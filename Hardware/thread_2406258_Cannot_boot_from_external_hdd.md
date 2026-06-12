---
title: "Cannot boot from external hdd"
date: 2018-11-18
forum: Hardware
---

### Post by g01d3n95 on 2018-11-18
Hello to You,
I will get straight to the point. I have tried installing Ubuntu 18.04 into my external hdd (WD My Passport 1TB). I have read that it is best to install the system with both clean internal ssd and external hdd and so I did that. Later, I had a problem with getting the installation of the system, but after changing SATA Controller Mode from AHCI to Compatible (IDE), and disabling my discrete gpu [UMA only] the installation went smoothly  (also I have no idea why I my gpu makes the whole screen still, meaning the mouse does not react and I cannot make anything). I installed Ubuntu Desktop from usb, btw.
The main problem is, however,  when I try to boot from the external hdd. I have set in the bios the boot order like this: 1. WD My Passport 25E1 2. Windows Boot Order 3. ATA HDD. I know for sure that that the system was correctly installed because I can boot from the WD on my older laptop and it works perfectly fine.
When I try to turn on the new laptop it seems that the laptop tries to boot from external hdd but cannot and then boots from the internal hdd.
I should also tell you that I have recently back flashed my bios to a previous version because of the performance issues and in both versions of the bios the problem with external hdd persists. So my question is simple, Can I do anything else to boot from the external hdd or is it impossible with this laptop?


My laptop specs:
Lenovo
Product Name: IP320-15AST
BIOS Version: 5PCN20WW
CPU: AMD A6-9220, RADEON R4, 5 COMPUTE CORES 2C+3G
System Memory: 4096 MB

Thanks in advance,
g01d3n95

---

### Post by oldfred on 2018-11-18
Is Lenovo new UEFI system but you installed to external in BIOS/MBR configuration?
Many manufacturers call UEFI as BIOS since users know that name, but all systems in last 5 years are UEFI.
Microsoft required UEFI with gpt partitioning on all new Windows systems when Windows 8 was released in 2012.

With external plugged in:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by g01d3n95 on 2018-11-18
I have tried Boot Repair and the link is: [http://paste.ubuntu.com/p/DcKdMzYFZQ](http://paste.ubuntu.com/p/DcKdMzYFZQ)

---

### Post by oldfred on 2018-11-18
You booted Boot-Repair in UEFI mode.
Report shows an sda, but nothing about it?
And sdb is external drive configured for BIOS boot on gpt partitioned drive as it has a bios_grub partition for grub to install to gpt's protective MBR and have additional boot code in bios_grub partition.
If you want UEFI boot, you have to have an ESP - efi system partition which is FAT32 with boot flag on sdb. It can be anywhere between 100 and 500MB. 

With external drives and UEFI, install becomes a bit of an issue.
UEFI only boots from ESP on external drive and /EFI/Boot/bootx64.efi.
But normal install of Ubuntu has a version of grub that only installs to first ESP, normally sda's ESP, not external drive or even sdb's, even if you specify that during install. (I just tried again with 19.04 and it still only installed into my sda's ESP).
My work around is to partition in advance using gpt & have ESP on sdb, external drive or flash drive. Then copy /EFI/ubuntu from sda to external drive twice. Once to /EFI/ubuntu & once ot /EFI/Boot and in /EFI/Boot rename shimx64.efi to bootx64.efi. I quick learned to backup my Ubuntu boot entry in sda as it overwrites that with every new install. If you only have Windows in sda, it will just add a new folder into sda's ESP.

---

### Post by g01d3n95 on 2018-11-18
i have no idea how to have ESP on sdb, tbh, but when flashing usb for install I have discovered GPT Partition Scheme. If you could tell me what to do next I would really appreciate it.
Also, I have completely erased all data from sda so I have no idea why it would show that.

---

### Post by g01d3n95 on 2018-11-18
I figured it out, I added efi reserved partition and it solved the issue. Now it runs perfectly fine. Thank you for the advice.

---

### Post by oldfred on 2018-11-18
If you erased all of data from sda, then that would be why it shows nothing.
Some reason to erase it?
Report is not good about showing NVMe drives, do you have one of those with Windows?

You can shrink sdb1 by 200MB with gparted and add a the ESP - efi system partition. It should be FAT32 with boot and esp flags. Right click on partition to add flags.

If you only have sda, you may need to use gparted to make it gpt partitioned and add an ESP to it. Or disconnect it. Then Ubuntu's grub will find an ESP to install its boot loader into. If you have NVMe drive, grub will probably create new folder in its ESP.
After creating ESP on external, run Boot-Repair, see if in advance mode it will install grub boot loader to external drive, but it may not.
If not we will have to copy from where ever it actually installed to external drive.

---

