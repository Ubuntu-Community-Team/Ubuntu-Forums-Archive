---
title: "Asrock 770 Extreme 4 - work with Ubuntu?"
date: 2012-11-25
forum: Hardware
---

### Post by mark2741 on 2012-11-25
Last night I upgraded/rebuilt my PC by changing to the following:

Asrock Extreme 4 motherboard
Core i3 3225 3.3GHz LGA 1155 processor
8GB RAM

Installed Windows 7 64 and set it up for my wife/kids (I know...), then popped in the Ubuntu 12.10 64-bit DVD and started the install. Partially through the install it threw an error saying that it couldn't add the bootloader on the primary drive (I have two drives, with SDA being Windows on it and SDB Ubuntu on one partition and a Shared FAT32 on the other). It made me pick another partition, so I chose the SDB.

It finished the install and then when I went to reboot, I lost everything....Windows included.

I think it might have something to do with this new-fangled 'UEFI' motherboard. 

Does Ubuntu work with this motherboard/UEFI? Anything I should do to get it working? I don't want to have to reinstall/setup Windows again.

---

### Post by oldfred on 2012-11-25
Did you install Windows in UEFI mode or BIOS mode?

Both Windows & Ubuntu need to be installed in the same mode and both should give you the choice when booting the installer. Some systems call BIOS mode legacy/AHCI or other names.

Best to see exact configuration you have. Boot-Repair can convert a BIOS install of Ubuntu to UEFI by uninstalling grub-pc and installing grub-efi.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

       UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

    
       AsRock calls BIOS mode AHCI.
Someone posted this on your AsRock system. Issues with Asmedia ports.
> "Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

---

### Post by mark2741 on 2012-11-25
Thanks for the response/info. I'm still not totally understanding, but I did look in the BIOS and the boot sequence is set to load the DVD, then HD, both in AHCI. I then googled and found a post on how to check if AHCI is enabled in Windows 7 and it appears AHCI is setup and working on my system (basically the page just said look in Device Manager under the IDE section and if an AHCI driver is installed then it is enabled and working).

Of course, this is after doing a completely clean install of Win 7 and installing tons of drivers with multiple reboots since last night. I'm not sure if it was setup as EFI boot last night, when the Ubuntu installer hosed the system, or not.

Just checked the link you provided for the "SecureRemix" and that looks great, but I'd much prefer to go straight to Ubuntu 12.10 if possible, versus the LTS. I will look and see if there is a 12.10 version of SecureRemix.

Thanks again.

---

### Post by Yellow Pasque on 2012-11-25
I doubt you lost everything. It sounds like you tried to overwrite the Windows bootloader with GRUB and it failed, so you put GRUB on the Ubuntu disk. However, you need to set your system/BIOS/EFI to boot the Ubuntu disk (you can fix the MBR of the Windows disk if you have a Windows CD).

---

### Post by oldfred on 2012-11-25
You can just install Boot-Repair to your Ubuntu liveCD/USB.

If you installed Windows and are using AHCI, you must be in BIOS mode. Boot-Info report will show details.

---

