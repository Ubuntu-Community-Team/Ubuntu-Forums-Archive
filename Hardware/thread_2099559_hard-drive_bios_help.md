---
title: "hard-drive bios help?"
date: 2012-12-29
forum: Hardware
---

### Post by ironhoof on 2012-12-29
I hope I posted this to the correct area:
Okay I have done quite a bit of research read a bunch of forums, including ubuntu UEFIbooting documentation. I have an ACER M3470G desktop  I got a year ago, and installed xubuntu on a second drive which worked  fine (which I now know worked because my current drive is MBR). Now that the year  is up I tried to use the drive that came with the machine. I used  efibootmgr utility and boot-reapir they both appeared to work , and when  checked they indeed changed the info. I restart the computer, and its  all changed back as if I did nothing. Which brings me to my readings on  secure boot and the "bios". The "bios" has nothing of the kind to enable  or disable this, instead it strangely has a list in boot options of the  AMI P01-A3 Rev 4.6:
1: [EFI Device]
2: HDD
3: CD
4: Removable media
5:LAN

Giving it some though I could move EFI Device down the list to the bottom but it changes nothing. I also read somewhere providing a supervisor password enabled the ability to turn it off, but I also see this doing nothing. Has anyone else had experience with this? (Note: I even tried converting the GPT drive to a MBR, but again when rebooted it changes it back) I read all about this ahead of time, and all this time I had one under my nose so annoying. -.- Anyone know of anyway I could utilize this drive?

efibootmgr also listed everything in strange order as the Linux disk was booted EFI but the hardrive was UEFI. I heard they cant mix? How can I erase the NVRAM with my own keys? doesn't appear to be enough info just the same info repeated.

---

### Post by oldfred on 2012-12-29
Just because a system has UEFI, it may or may not be booting with UEFI or legacy/BIOS/AHCI/CSM or whatever. 

Only new systems with Windows 8 pre-installed have secure boot, so you should not have to worry about that.
How you boot install media - UEFI or BIOS is how system will install for both Windows or Ubuntu.
Some Windows 7 systems are UEFI, but most were BIOS. Ubuntu has has UEFI capability for several versions, but 12.10 is the most up to date and works with the new secure boot UEFI.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by ironhoof on 2012-12-29
Well ok, I geuss the first step is to give you this then from boot-repair:
[http://paste.ubuntu.com/1470561/](http://paste.ubuntu.com/1470561/)

BTW i have no intention of using windows, so completely eliminating it is desirable. Although im sure the likely the only thing that remains is the .efi for it.

---

### Post by oldfred on 2012-12-29
You are still showing the Windows efi files in the efi partition. I thought the UEFI read the efi partition to know what to boot, but it seems that it saves that data. 

Some UEFI's have the UEFI shell built in or an efibootmgr, so you can edit parameters. Others can add the Intel one. Once you set ubuntu as boot choice you should get that as the default when rebooting. Then you can use one time boot key or UEFI menu to change boot if you want to boot flash drive or DVD.

       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

    
You cannot mix UEFI and BIOS. 

And UEFI usually had gpt partitioned hard drive per its spec. BIOS should not even work. 
But Ubuntu will boot from a gpt drive with BIOS as that is what I have. But Windows will not, it only boots from gpt drives with UEFI.

---

