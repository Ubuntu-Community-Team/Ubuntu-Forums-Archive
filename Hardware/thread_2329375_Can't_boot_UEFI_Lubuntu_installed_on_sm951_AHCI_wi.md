---
title: "Can't boot UEFI Lubuntu installed on sm951 AHCI with SATA=RAID"
date: 2016-06-30
forum: Hardware
---

### Post by megahertz2 on 2016-06-30
I have a Z170-HD3P MB with 2x4G 3000 DDR4 memory, a Samsung 128G 951 AHCI M.2 drive and 2 WD 500G HDD.
On the UEFI BIOS; OS is set to Other, and boot options and other drives are set UEFI Only.
With the two WD 500G HDD, I’ve created a RAID 0 array to use as drive D:, so I’d also set SATA to RAID on the UEFI BIOS.
 
During Windows 7 installation, after loading SATA, AHCI, RAID and USB 3 chipset drives, I partitioned the 951 AHCI M.2 drive for Windows (EFI, MS reserved and for C:) and left two other partitions for Lubuntu (EXT4 and Swap). During Windows 7 installation I moved the users folder to drive D:, (RAID 0 array). Windows 7 is working well.
 
When I tried to install Lubuntu 16.04 using a USB UEFI pendrive it couldn't "see" my 951 AHCI M.2 drive.
So I tried another approach. After detaching the two WD 500G HDD (now on a RAID 0 array), I’ve set SATA to AHCI on the UEFI BIOS.
 After booting Lubuntu using the USB UEFI pendrive it **could** see" my 951 AHCI M.2 drive and I've installed Lubuntu without problems.
The problem is that it ONLY works with SATA = AHCI on the UEFI BIOS. With SATA = RAID it loads Grub but doesn’t boot, I guess because GRUB doesn't see my 951 AHCI M.2 drive when SATA = RAID.
With SATA = AHCI, I’ve booted Lubuntu and installed Dmraid, but it didn’t help.
 
My question for the Linux experts:
As I need to have SATA = RAID so the two WD 500G HDD (now on a RAID 0 array) be able to work, what I have to do on Lubuntu to get it working with the UEFI BIOS:
- OS set to Other.
- Boot options and other drives set to UEFI only.
- SATA set to RAID.
 
EasyUEFI (in Windows) shows that I have two options to boot Lubuntu:
- File path:\EFI\UBUNTU\SHIMX64.EFI
- File path:\EFI\UBUNTU\GRUBX64.EFI
With one should be used?
 
If someone has the answers, please explain in a manner that a non-Linux expert can understand and apply. Thank you.

---

### Post by oldfred on 2016-06-30
Is M.2 SSD seen as SATA or the new NVMe device?

My M.2 SSD (SATA)just worked with 16.04 with my Z170 motherboard.
If booting from SSD, then RAID should not be a factor as that is not part of RAID.

Shim is the secure boot version of grub or the shim between standard grub & signed files. If you have secure boot off either grub or shim should work. But if UEFI Secure boot is on, only shimx64.efi will let you boot if you have signed kernels & other files.

RAID 0 is not recommended. And if just your data drive, it does not add any real speed to system.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by megahertz2 on 2016-06-30
As I wrote, my 951 M.2 drive is AHCI, not NVMe. I don't know how Lubuntu see's it. The fact is, as you mentioned, it is not part of a Raid array, so SATA=RAID should not be a problem. But it is. With SATA=AHCI it boots. With SATA=RAID it doesn't. Try to set SATA=RAID on your MB to see if it boot's Ubuntu.

For all I had read, the problem is SATA=RAID that prevents the SM951 (and others M.2 drives) to been seen by Ubuntu. It's a Bug?

---

### Post by oldfred on 2016-06-30
BIOS based RAID does not boot from MBR, but from /dev/mapper.
But you should be using UEFI and then you boot from the ESP - efi system partition.
Do not know if you can set SSD as AHCI and use RAID for hard drives? Normally BIOS RAID uses two drives and both are part of the RAID.

Default install of Windows 7 from DVD is BIOS, but with new UEFI hardware you should be using UEFI.
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html

      [/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    [URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]
[/URL]

---

### Post by megahertz2 on 2016-07-01
First of all, this is not only a problem on my system. I've seen many similar descriptions on this forum and in many other forums. And I'm sure that it is related to SATA=RAID.
My system is configured right.
On the UEFI BIOS; OS is set to Other, and boot options and other drives are set UEFI Only.
The SM951 and the RAID array are UEFI and GPT formatted.
Windows 7 has been installed with a UEFI USB pendrive (loaded with USB3 and SATA and AHCI drives) on SM951 as UEFI with SATA=RAID and is working well.
Lubuntu 16.04 has been installed with a UEFI USB pendrive on SM951 as UEFI with SATA=AHCI and is working well.

The problem is, with SATA=RAID, when Lubuntu 16.04 is booted from a UEFI USB pendrive it **can **see my RAID array but can't see the SM951. It means that some kind of command or drive is missing so the OS can see the SM951 AHCI drive.
On the installed Lubuntu, UEFI Grub (on \EFI\UBUNTU\GRUBX64.EFI) is loaded but Lubuntu doesn't launch.
I'm sure that something is missing on the Linux OS. It can be a command or a drive. When we find a way so that the Lubuntu 16.04, booted from a UEFI USB pendrive, **can **see the SM951 with SATA=RAID, we would have fond the solution.

---

### Post by sudodus on 2016-07-01
Have you tried to install Ubuntu Server? You can try to install a very basic system (with only text screen user interface and no particular server package installed, only the default). This is a rather quick process, and since you suspect that something is missing in Lubuntu, chances are that you have better luck with the Ubuntu Server.

If the installed system work (after reboot), you can install Lubuntu

[sudo apt-get install lubuntu-desktop](sudo apt-get install lubuntu-desktop)

and it should continue to boot. If there are problems, they are likely about drivers for graphics or wifi.

---

### Post by oldfred on 2016-07-01
Part of issue may be AHCI mode would not have any RAID drivers or RAID settings in grub.

I believe dmraid has been replaced with admdm:

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

Grub also has several mdraidxx.mod that you may need one of loaded in grub?

---

### Post by megahertz2 on 2016-07-02
I tried to use the lubuntu-16.04-alternate-amd64, with the UEFI BIOS: SATA=RAID, OS is set to Other, and boot options and other drives are set UEFI Only, but it can see my Raid array but **can't** see the SM951.
As Lubuntu 16.04 is already installed on SM951, partition 4, i've tried some bios combinations:
- UEFI BIOS: SATA=RAID, OS is set to Other, and boot options and other drives are set to UEFI = Grub is loaded but Lubuntu doesn't launch.
- UEFI BIOS: SATA=RAID, OS is set to Other, and boot options and other drives are set to **Legacy **or **Disable **= Grub is loaded and Lubuntu launch normally. I do have access to RAID array, but it doesn't launch Windows.
- - UEFI BIOS: SATA=AHCI, OS is set to Other, and boot options and other drives are set **to UEFI, Legacy **or **Disable **= Grub is loaded and Lubuntu launch normally. I do **NOT **have access to RAID array, so I can't use or launch Windows.

Until someone finds a solution for the combination Lubuntu+SATA=RAID, OS is set to Other, and boot options and other drives set UEFI, I've created two BIOS profiles:
To be used with Windows: SATA=RAID, OS is set to Other, and boot options and other drives are set UEFI
To be used with Lubuntu: SATA=RAID, OS is set to Other, and boot options and other drives are set to **Disable**

---

### Post by oldfred on 2016-07-02
I do not think Boot-Repair will fix your problem.
It just may be the combination of RAID settings in UEFI and install.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by megahertz2 on 2016-07-02
Thank you for your help.
With OS set to Other, SATA set to RAID, Boot options and other drives set to UEFI only.
Grug is loaded but Lubuntu doesn't launch 
The bootInfo is on [https://paste.ubuntu.com/18344195/](https://paste.ubuntu.com/18344195/)

With OS set to Other, SATA set to RAID, Boot options and other drives set to Legacy only.
Grug is loaded and Lubuntu launch
The bootInfo is on [https://paste.ubuntu.com/18425228]("https://paste.ubuntu.com/18344195/")

---

### Post by oldfred on 2016-07-02
My SSD on a M.2 port comes up as sda. 
Normally on my other systems, I have to make sure boot drive is sda or SATA port 0.
I have skipped SATA ports and had issues.

I might see if you can change drive order, but do not know if possible with M.2.

Part of issue is that grub in UEFI mode only installs to sda. I have seen other RAID configurations were standard SSD was boot drive and sda without issue.

Did you install without RAID drives plugged in?

Error: The backup GPT table is not at the end of the disk
Have seen this error with LVM where LVM spans two drives and then gpt gets confused. But other cases are where Windows partitioned drive incorrectly.
Often just use gdisk and resaving partition table resolves it, but do not know with RAID, if you can do that.

---

### Post by megahertz2 on 2016-07-04
That's it. On my MB the SM951 M.2 isn't part of the SATA disks. It is a separate controller tab, where is only information, no settings.
But why it only doesn't work with SATA=Raid _and _UEFI?
SATA=Raid and Legacy or SATA=AHCI and UEFI it does.
I had a similar issue when installing Windows 7. I could only see the SM951 M.2 drive after loading the new AHCI and SATA drives. I think these new drives must also be loaded into Ubuntu or even the Kernel.

---

