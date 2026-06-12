---
title: "Figuring out UEFI and secure boot"
date: 2014-08-16
forum: Hardware
---

### Post by elric3 on 2014-08-16
Just purchased a new desktop computer, specifically to be used for high quality photo work; it came with pre-installed Windows 8. (Asus essentio desktop m51ad-b05, with an intel i7-4770s) I do not want Dual boot windows, just Ubuntu Studio and I'm having problems booting the Ubuntu installer...I think the problem is from UEFI or secure boot. I want to know if this is possible with this hardware? 

So far I have tried:

1) [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).... followed to item 2. and disabled FastStartup in Windows 8, disabled FastBoot in BIOS, enabled CSM mode
2) Booted using Linux Mint 17, erased entire hard drive. Formatted it with 3 partitions for Linux install. 
3) Installed Linux mint 17. Rebooted, but would not get past BIOS
4) Tried to boot Live DVD Ubuntu Studio 14.04.1. Boot menu works. Picked try using Ubuntu without installing option. Shows blue boot splash screen with spinning circle. Circle dissappears, splash screen stays and is stuck. This also happens if I choose Install Ubuntu option, or if F6 nomodeset is selected, or other F6 options.
5) Tested the Live DVD, checked install media said it was good. Made live USB, just in case..., same results as live DVD (step 4).
6) Turned off CSM and booted Live DVD in UEFI mode...same results as step 4. ([http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295))
7) Tried a few other BIOS options, still no luck. Unable to figure out how to disable Secure Boot from within BIOS

Here's the screen shots: [http://goo.gl/oTJ3Ac](http://goo.gl/oTJ3Ac). Here's the basics

Asus UEFI BIOS utility advanced mode
BIOS version 0507 x64
Build date 04/02/2014
ME version 9.0.13.1402
South Bridge Stepping 05/C2
Bottom of Screen: Version 2.10.1208. Copyright AMI

Contemplating my options:
1. Can I put Ubuntu Studio on this hardware? (I prefer this choice)
2. If I return this, and get store credit, are there any current desktop systems more compatible with Ubuntu Studio 14?
3. If not, would this be easier if I bought the motherboard and components separately?
4. Is it possible and/or advisable to flash the BIOS and therefore not have to deal with secure boot? (This sounds kind of scary)


Any help? Much appreciated :)

thanks
Elric McGee III

---

### Post by weatherman2 on 2014-08-16
BIOS/EFI firmware are made specifically for various motherboards.  One can't simply install a different BIOSof choice .  Chances are you will ruin the motherboard - "brick it" - if you try that.  You will most likely need to use whatever Asus provides.

You could look on the Asus website and find the support page for your computer and see if there is an updated BIOS newer than the one you have installed on your computer and install the newer version.  I believe new hardware has the ability to flash an updated BIOS using a USB thumb drive, without booting an operating system (as it sounds like you have erased Windows 8).  An updated BIOS, if one is available for your computer, might fix some of your issues.  Maybe not.

If you build your own custom system with your own chosen components, you would likely have more options for booting and disabling secure boot, etc.  Even then, you should still choose something that has known good Linux compatibility.

I can't give you any specific tips for booting one version of Ubuntu on this hardware when another version of Linux (Mint 17) boots without problem - at least, the live version does.  I have a motherboard that has the same issue: I can't boot Ubuntu 14.04 on it at all but Ubuntu 12.04.3 boots without issue.  Perhaps there is a workaround - but for the moment, I simply gave up and stuck with 12.04.3 which works fine and is supported another few years.  (For me, booting 14.04 wasn't anything to do with secure boot - i have installed 14.04 successfully on other systems.)  This particular motherboard/chipset has issues with 14.04 so I gave up that option for now.

If you really want Ubuntu Studio 14, then your choices are to spend a lot of troubleshooting time trying to get it to boot on this hardware, try a different version of Linux, or return this computer and try another one.   I can't recommend anything new - find cases where people say they have installed 14.04 successfully.  Some computer stores will let you boot Linux live USB drives on their demo computers to test them out, so you might be able to try and boot something in a store before buying that model.

As for Mint 17: if you were able to install but just can't boot, I think you are close and could probably get that going, if you are open to using a different version of Linux (or an older version of Ubuntu Studio perhaps).

---

### Post by oldfred on 2014-08-16
It looks like your specs include a nVidia card. 
Are you booting with Intel internal chip or nVidia?

With my much older nVidia I have to always use nomodeset for live installer, and first boot or until I install nVidia drivers from the repository.

Boot with UEFI or after install will be grub menu edit. If BIOS your use f6.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If installing only Linux not Windows still better to use gpt partitioning and include the efi partition even if not used now, so you can use it later if desired. Very difficult to add to beginning of drive after drive has lots of data. Windows requires gpt partitioning to boot in UEFI mode. And with BIOS normally MBR(msdos) is used. But Ubuntu can boot with either UEFI or BIOS if correct supporting partitions are on drive. For UEFI you need the efi partition and for BIOS boot you need the bios_grub partition.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

