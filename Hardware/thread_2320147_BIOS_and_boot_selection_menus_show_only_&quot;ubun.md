---
title: "BIOS and boot selection menus show only &quot;ubuntu&quot; as a device"
date: 2016-04-11
forum: Hardware
---

### Post by hicoleri on 2016-04-11
I had been dual booting Windows 8 (preinstalled) and Linux Mint on my laptop for about half a year. I recently wanted to install Xubuntu on it. When I plug in my flash drive and try to boot from it (by pressing F-10 on startup) the device selection menu shows "ubuntu" as the only device. I have tried the flash drive in other computers and it works perfectly well.
The BIOS ("Phoenix SecureCore") also lists "ubuntu" as the only device in the boot order dialogue, however, it does detect the harddrive and the disk drive in the computer (visible in the default dialogue).

[IMG]https://s29.postimg.org/8bza27zon/IMG_20160411_105709.jpg[/IMG]

I have tried resetting the BIOS (from the options from the BIOS), running testdisk (which revealed cluster mismatches and bad sectors), and run fsck on the linux partition with no success. I have been unable to boot from any other device, and disabling "ubuntu" from the BIOS results in repeated halting and starting of the system.

What should I do to fix this?

Hardware info: [http://paste.ubuntu.com/15753417/](http://paste.ubuntu.com/15753417/)

---

### Post by oldfred on 2016-04-11
Did you install Ubuntu in UEFI or BIOS boot mode.
The two modes are not compatible.
So you may have Windows in UEFI that will not see Ubuntu.
And Ubuntu in BIOS mode that will not see Windows.

Boot-Repair can convert a BIOS install on gpt drive to UEFI boot using its advanced mode, if booted in UEFI mode.
How you boot install media is how it installs.
       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

      [/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) 

  These are now older versions of Ubuntu, but install (and issues) should be similar:

 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by hicoleri on 2016-07-21
Sorry for the extremely late response.

The problem lies with the UEFI firmware, and Ubuntu lists itself as the entry on top of all the devices.
It was solved by, first of all, removing the 'ubuntu' entry from the efi 'boot' list, by using efibootmgr ([FONT=courier new]sudo [/FONT][FONT=courier new]apt install[/FONT][FONT=courier new] efibootmgr[/FONT]), [as according to this answer]("http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi")  and then deleting the ubuntu folder from /boot/efi/EFI/, to prevent the  UEFI firmware from deleting them. However, this prevents the computer  from booting, because the computer does not have anything to boot  anymore.

A workaround to this is installing a boot manager, namely [refind]("http://www.rodsbooks.com/refind/"),  which I have been using. It does not mess around with the UEFI  partition, and simply lists available devices which can be booted.
There may be better solutions but I have not bothered because this is working for me.[URL="http://www.rodsbooks.com/refind/"]
[/URL]

---

