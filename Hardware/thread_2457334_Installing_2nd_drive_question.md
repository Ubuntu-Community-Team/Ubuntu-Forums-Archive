---
title: "Installing 2nd drive question"
date: 2021-01-30
forum: Hardware
---

### Post by jmichaels29 on 2021-01-30
If I leave my HD in my system and install an SSD and install Ubuntu on the SSD.
To make the SSD be the boot drive, will I need to select that when installing Ubuntu, or would I do that in the bios ?
Later, I would format the HD, and use it as a backup drive.

---

### Post by Yellow Pasque on 2021-01-31
You set the boot order in the BIOS/EFI. Just make sure you select the correct disk when running the installer. If it's not too much trouble, I would unplug the data cable from the HD before running the installer. That will minimize the risk of installing to the wrong disk.
After install, shut down the system, and replug the HD. Boot (the SSD) into the new installation of Ubuntu and run 'sudo update-grub'. Now, you should be able to boot whatever OS(s) are on the HD from GRUB instead of having to boot into the HDD directly.

---

### Post by jmichaels29 on 2021-01-31
Questions about "Sudo update-grub"

So, after the installation, should I go to bios and select the new SDD to boot.  Then go to terminal and do the sudo update-grub, and it will do this grub update on the new drive?

Also, once I format the old drive, will it show up on the dashboard/dock?

---

### Post by CelticWarrior on 2021-01-31
A few things to consider:
Firstly, you intend to use the old HDD as data storage only, not to run any other OS, then you don't need the "update-grub" step. And yes, once formatted it'll show up like any other data only drive, internal or external. For the intended purpose it won't be different than an USB connected HDD or flash drive.

Regarding the boot process BIOS and UEFI are different, you must know which one you have in order to properly manage the boot process.
BIOS boots drives, it reads the MBR of the first boot device and releases control to whichever bootloader is there (it can be only one).
UEFI boots EFI bootloaders that are in the ESP (EFI System Partition), a small FAT32 partition typically at the beginning of the first drive in the boot order menu.
Unless you have a very old - pre-2012 - computer it has UEFI instead of BIOS.

Now, assuming you follow the instructions in post #2 - disconnect or disable the old HDD in UEFI("BIOS") - then the new SSD will be the one and only drive where to install Ubuntu. Reconnecting or re-enabling the old HDD shouldn't change the boot order but double check it anyway.

For better results (and assuming it is UEFI) make sure you have UEFI only as the boot mode: Disable CSM/Legacy boot mode (don't confuse it with legacy USB support, keep this one enabled, as many computers don't boot from the USB installer with legacy USB support disabled) to assure the installer / live session boots and install in UEFI mode.

Prepare the new drive correctly: GPT is preferred. In the live session, before starting the installation, open GParted and make sure the SSD is selected. Then go to the Device menu > Create new partition table and select "GPT".

Now for the actual installation you have two options, automatic or manual partitioning ("something else"). Considering the questions you're asking, please choose the automatic option.

Once done reboot when prompted and assure the newly installed system is booting properly. If so all the correct UEFI settings were automatically set. At the UEFI settings > Boot menu (or equivalent) you should find one submenu that deals with drives/disks boot order and there the SSD should be the first (that's where the ESP resides) and another submenu for OS selection where you should see "Ubuntu". Then reconnect or re-enable the old HDD and again confirm in UEFI settings > Boot that the boot settings haven't changed, adjust if needed (most likely it won't be).

Finally boot into your newly installed Ubuntu again and, for convenience, use Disks to create and format one or more partitions in the old HDD. I said for convenience because although there are dozens of methods to achieve the same goal, Disk is practical, intuitive, and automatically sets the ownership of the new partition to your own user. Please note that for data only drives GPT or MBR doesn't matter much.

---

### Post by Yellow Pasque on 2021-01-31
Thank you for saving me the typing, CelticWarrrior

---

