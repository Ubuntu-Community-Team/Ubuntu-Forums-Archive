---
title: "Does Asrock 970 Extreme3 allow dualbooting Windows and Ubuntu easily?"
date: 2013-03-09
forum: Hardware
---

### Post by thunderpenguin on 2013-03-09
Hi

I am building a new PC which will dualboot Windows 8 and Ubuntu.

I am thinking of getting an Asrock Extreme3 motherboard which has UEFI.  [http://www.asrock.com/mb/AMD/970%20Extreme3/](http://www.asrock.com/mb/AMD/970%20Extreme3/)

I want to know if I can easily dualboot Windows 8 and Ubuntu with this motherboard.

[http://www.asrock.com/mb/AMD/970%20Extreme3/](http://www.asrock.com/mb/AMD/970%20Extreme3/)

This webpage says it works on Linux but doesn't say if it can dualboot Windows 8 and Linux [http://community.linuxmint.com/hardware/view/12913](http://community.linuxmint.com/hardware/view/12913)

Please tell me if this motherboard can easily dualboot Windows 8 and Linux

---

### Post by oldfred on 2013-03-09
It says it supports Windows 8. If you install yourself, you should not have the issues of secure boot, but have to be sure to install both Windows & Ubuntu in UEFI mode. And how you boot installer is how each installs. Windows only boots with UEFI from gpt partitioned drives, but Ubuntu will boot in BIOS/Legacy mode with gpt partitioning.

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

 Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Only use Windows disk tools to shrink Windows NTFS partition but not to create any new partitions for Linux. Not sure with gpt if it still will convert to dynamic or not but you do not want dynamic partitions as that does not work with Linux.

Even if you do not have the secure boot issues, you need the newest grub2 versions of UEFI boot.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some users have reported issues with creating gpt partitioning with Windows and Linux Disk Utility. If drive is over 2TB use gdisk, otherwise use gparted to make drive gpt. It seems that backup gpt partition table should be at end of drive, but some tools put it in the middle or on 3TB drives do not put it at the end. If not at end correctly then partition may overlap backup partition table and cause all sorts of issues. But it may only be an issue where one very large partition is created as that is what we have seen so far.

---

### Post by thunderpenguin on 2013-03-09
Thank you oldfred for your help. I'll read those links carefully.

A person on this webpage got Asrock 970 Extreme3 to dualboot Windows 7 and Ubuntu 11.10.

[http://forum.dune2k.com/topic/24153-new-emperor-server/](http://forum.dune2k.com/topic/24153-new-emperor-server/)

I emailed him to ask about how he did it.

---

### Post by oldfred on 2013-03-09
Different model:
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

Again a different model, but read entire article as it seemed a too heavy cooling fan bent motherboard & damaged CPU. Then that CPU damaged more motherboards?
[http://www.tomshardware.com/reviews/build-a-pc-tahiti-le-crossfire-overclocking,3454.html](http://www.tomshardware.com/reviews/build-a-pc-tahiti-le-crossfire-overclocking,3454.html)

some have posted this info also:

 AsRock calls BIOS mode AHCI.
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

---

### Post by thunderpenguin on 2013-03-17
Hi

I decided to buy the Asrock 970 Extrem4 motherboard and I also bought the rest of my parts.

I hope I can get Windows 8 and Linux dualboot installed easily.

I decided to buy the Asrock 970 Extrem4 motherboard and I also bought the rest of my parts.

I hope I can get Windows 8 and Linux dualboot installed easily.

Edit:

I got the computer assembled and attached the peripherals.

The Asrock 970 Extreme4 motherboard seems to be working fine so far.

Secure boot was already disabled and installing Windows 8 and Ubuntu 12.10 dualboot was not any more difficult than dualboots I've installed on non-UEFI motherboards.

---

