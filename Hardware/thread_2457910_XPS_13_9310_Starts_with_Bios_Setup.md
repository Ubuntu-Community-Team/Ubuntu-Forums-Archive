---
title: "XPS 13 9310 Starts with Bios Setup"
date: 2021-02-12
forum: Hardware
---

### Post by igorlopez on 2021-02-12
Hi I have a new (2 weeks old) DELL XPS 13 9310 i7-1165G7 512 GB SSD

The Laptop was purchased as a Windows 10 machine (Ubuntu variant is still not available here) 
but Canonical has certified this specific variant (HW vise at least but with a different BIOS version).

Ubuntu 20.04 works as expected when trying without installing.
Install goes through without any visible issues but when it reboots DELL just ends up in the BIOS Setup program.

Note, this is not a dual boot setup, e.g. there are no more Windows at all on the disk.

BIOS Version: 1.2.5
SATA/NVMe is configured for AHCI/NVMe

I have tried to add own Boot options in the setup and tried the different EFI files on the disk both with and without Secure Boot turned on.

**Secure Boot ON** ------------ **System Response**
EFI/ubuntu/shimx64.efi ---- Returns to Bios Setup
EFI/ubuntu/mmx64.efi ----- Returns to Bios Setup
EFI/ubuntu/grubx64.efi ---- Operating system has no signature: Incompatible with Secure Boot verification:F1-Retry,F2-Reboot,F5-Onboard Diag
EFI/BOOT/BOOTX64.efi -- System BootOrder not found. Initializing defaults
EFI/BOOT/fbx64.efi -------- Operating system has no signature: Incompatible with Secure Boot verification:F1-Retry,F2-Reboot,F5-Onboard Diag
EFI/BOOT/mmx64.efi ----- Returns to Bios Setup

**Secure Boot OFF** ----------- **System Response**
EFI/ubuntu/shimx64.efi ----- Returns to Bios Setup
EFI/ubuntu/mmx64.efi ------ Shim UEFI key management:Perform MOK management:Enroll key/hash from disk
EFI/ubuntu/grubx64.efi ----- Returns to Bios Setup
EFI/BOOT/BOOTX64.efi -- System BootOrder not found. Initializing defaults
EFI/BOOT/fbx64.efi --------- System BootOrder not found. Initializing defaults
EFI/BOOT/mmx64.efi ------ Shim UEFI key management:Perform MOK management:Enroll key/hash from disk

Any ideas?

---

### Post by vanadium on 2021-02-12
Go into BIOS. Somewhere the drive protocol will be set to RAID - change this to (I think) SATA and it should boot.

---

### Post by igorlopez on 2021-02-12
I specifically wrote: SATA/NVMe is configured for AHCI/NVMe
that is the same as RAID is not selected.
I can start Ubuntu live and it works and the installation seems to work as expected but when it reboots it goes into DELL Bios setup program.

---

### Post by oldfred on 2021-02-12
Have you updated UEFI and SSD firmware.
Many Dell systems have needed that.

Boot should be /EFI/ubuntu/shimx64.efi whether UEFI Secure boot on or not.
The grubx64.efi should work but only with Secure Boot off.
The /EFI/Boot/bootx64.efi is a copy of Windows .efi file originally & then a copy of shimx64.efi. It is a fallback or hard drive boot entry.

The mmx64.efi is the mokmanager and should only be required if you are booting in Secure boot mode and need to create your own key for a proprietary driver that does not have a Secure Boot key.

Is this your system? With new Intel graphics?
Dell XPS 13 9310 Intel Xe Graphics' Incredible Performance Uplift From OpenCL 
[https://www.phoronix.com/scan.php?page=article&item=intel-xe-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-xe-graphics&num=1)

---

### Post by igorlopez on 2021-02-12
Yes, that is my system and I have run the Dell Update when it still was a Windows PC.
I did not check what it updated but it did update the SupportAssist OS Recovery so I could at least test reinstalling Windows before installing Ubuntu.
Canonical has certified it but the BIOS version was Dell 0.2.11 whereas my PC has BIOS version Dell 1.2.5
As I wrote in my first statement, I tried all different .efi files located under the EFI folder both with and without Secure Boot.
There might be more options that needs to be turned ON or OFF but I am at loss figuring out what to do.
Eventually I'll return it since we have 30 days free return policy here.
I can get the XPS 13 7390 already installed with Ubuntu from another dealer so it might be my solution.

---

### Post by oldfred on 2021-02-12
If you can boot live installer in live mode run this, it may not tell anything if it is UEFI settings that need to be changed. But we can confirm install is correct.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I think the Phoronix tests used a much newer Kernel & other software.
While I normally suggest always using the most current LTS version, you may be an exception.
When I had a very new system in 2016, I had to install in February the release scheduled for April, then 16.04 using daily release. Re-installed after release to houseclean the many updates before official.

You can try 20.10 or the 21.04 daily.
I use an existing ISO, rename to versions I am downloading, so I do not download entire ISO again.


This is for Kubuntu which I now use, you have to change path if you want Ubuntu's daily.
I change to folder with my ISO, and copy/rename ISO I have.
 [noparse]zsync http://cdimage.ubuntu.com/kubuntu/daily-live/current/hirsute-desktop-amd64.iso.zsync
zsync http://cdimage.ubuntu.com/kubuntu/releases/20.10/release/kubuntu-20.10-desktop-amd64.iso.zsync
 [/noparse]
You can select here for Ubuntu daily.
[http://cdimage.ubuntu.com/ubuntu/daily-live/](http://cdimage.ubuntu.com/ubuntu/daily-live/)

---

### Post by igorlopez on 2021-02-12
Ok, I'll try a new install tomorrow (PC is back to Win10 again) and then I'll run the live installer to check.
Thanks for looking into this. I like the HW and it would be nice if I can keep it.

---

### Post by igorlopez on 2021-02-13
Well guess what !!!
I just read that there was a bug in the Ubiquity installer in 20.04.2 when installing in OEM mode (which was my first attempt that failed but I made several normal reinstall afterwards) with wifi connected.
This was something I did not know about before so all my install attempts have been with wifi connected.
This morning I tried the OEM install again but without wifi and voila it rebooted into Ubuntu.

Thanks for the guidance

---

