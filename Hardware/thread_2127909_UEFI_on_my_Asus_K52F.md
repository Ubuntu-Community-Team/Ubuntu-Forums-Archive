---
title: "UEFI on my Asus K52F"
date: 2013-03-21
forum: Hardware
---

### Post by Unstoppable36SG on 2013-03-21
Hey everyone :mrgreen: !  As the title says, I want to make the change from the basic BIOS to UEFI. It has the Intel® HM55 Express Chipset, among a WD7500BPKT 7200RPM HDD with Advanced Format, and 4 GB's of RAM, so it can run 64 bit operating sytems. I am very new with this, I did find out about UEFI because of Windows 8 and from my BIOS settings, where it is given the option: ' Activate UEFI Boot '. Anyway, I was planning a system reinstallation, so I am prepared for a HDD wipe, after which I would firstly install Windows 8 and then dual boot a Linux :D - maybe Ubuntu, I'll start another thread to find out if I should pick up Ubunto or another Linux distribution :)  So how do I do it? How do I make the switch from BIOS to UEFI ? :guitar:

---

### Post by oldfred on 2013-03-21
Windows installer has to be UEFI capable, not sure what versions of Windows are. But how you boot install media is how it installs. So if you boot Windows USB flash drive in UEFI mode it will install with UEFI. Same with Ubuntu, if you boot installer, it will install in UEFI mode.

Drive will have to have gpt partitioning, not the older MBR(msdos) partitioning.

If not a Windows 8 system pre-installed you should not have any issues with secure boot.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)


  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

      
     You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
    Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
    Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
    [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
    As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3. Details:
    [https://wiki.ubuntu.com/PrecisePango.../UbuntuDesktop](https://wiki.ubuntu.com/PrecisePango.../UbuntuDesktop)

---

