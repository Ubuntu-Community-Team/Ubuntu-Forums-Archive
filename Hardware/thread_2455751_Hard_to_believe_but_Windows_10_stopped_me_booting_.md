---
title: "Hard to believe but Windows 10 stopped me booting Ubuntu live from a USB"
date: 2020-12-26
forum: Hardware
---

### Post by welshmike on 2020-12-26
Fixing the more than annoyance, the start of the fix was to be remove PC battery and CMOS battery, etc..
 I do love Windows ... not.Grrrr

---

### Post by CelticWarrior on 2020-12-26
> [h=1][Hard to believe but Windows 10 stopped me booting Ubuntu live from a USB]("https://ubuntuforums.org/showthread.php?t=2455751")[/h]

It didn't.

---

### Post by welshmike on 2020-12-26
I wondered if the BIOS had been changed by Windows. As you wrote "It didn't" stop me (until I was able to open my laptop by removing a few screws)

---

### Post by hikariws on 2021-01-06
Secure Boot maybe?

---

### Post by welshmike on 2021-01-07
Ah yes thanks. 

Long post follows sorry, and see [https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2:](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2:) and my"quotes" from there.

I knew about such but hadn't thought that was it. 
I'd bypassed the problem by crashing Windows 10.
Perhaps because W10  now "boots" quickly it changes the UEFI so fast boot happens? 
Also "**PC makers have slowly been replacing BIOS with the Unified Extensible Firmware Interface**" (UEFI). 
That's all well and good, but one UEFI feature, " **Secure Boot, could be used to lock PCs into being only able to boot one operating system: Windows 8**" (and Windows 10). 
See this old article 
[https://www.computerworld.com/article/2826910/goodbye-bios--hello-uefi.html](https://www.computerworld.com/article/2826910/goodbye-bios--hello-uefi.html) .
Surely It can’t be Microsoft being determined to maintain its near monopoly of PC use?
“**In 2011, Microsoft announced that computers certified to run its Windows 8 operating system had to ship with Microsoft's public key enrolled and secure boot enabled. Following the announcement, the company was accused by critics and free software/open source advocates (including the Free Software Foundation) of trying to use the secure boot functionality of UEFI to hinder or outright prevent the installation of alternative operating systems such as Linux!**"
See 
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot_2)  Secure Boot section.
Also from Wiki
“Some PC manufacturers’ had hard coded firmware” (re UEFI) .
**“Firmware problems**
The increased prominence of UEFI firmware in devices has also led to a number of technical problems blamed on their respective implementations.[150] 
Following the release of Windows*8 in late 2012, it was discovered that certain Lenovo computer models with secure boot had firmware that was hardcoded to allow only executables named "Windows Boot Manager" or "Red Hat Enterprise Linux" to load, regardless of any other setting.[151] Other problems were encountered by several Toshiba laptop models with secure boot that were missing certain certificates required for its proper operation.[150] 
In January 2013, a bug surrounding the UEFI implementation on some Samsung laptops was publicized, which caused them to be bricked after installing a Linux distribution in UEFI mode. While potential conflicts with a kernel module designed to access system features on Samsung laptops were initially blamed (also prompting kernel maintainers to disable the module on UEFI systems as a safety measure), Matthew Garrett discovered that the bug was actually triggered by storing too many UEFI variables to memory, and that the bug could also be triggered under Windows under certain conditions. In conclusion, he determined that the offending kernel module had caused kernel message dumps to be written to the firmware, thus triggering the bug.[44][152][153] “

---

### Post by CelticWarrior on 2021-01-07
Those "news" are so old they stink... Badly.

Actually UEFI has great advantages for multi-booting and it was a necessary move from the old 1981 BIOS standard due to the complexity of the new hardware.
Unfortunately many people didn't understand UEFI back them and some even now, this thread is a case in point.

Here's what you need to know:
[LIST=1]
[*]The ability or lack thereof to boot external media has nothing to do with the installed OS, it has to do with improper media and/or user error.
[*]Yes, OSes can interact with the new firmware (UEFI) a lot more than they could with the old one (BIOS). Namely OSes can and often do change the boot order. That's how Ubuntu can give priority to Grub without the users needing to go back to the firmware settings after installation (doesn't always work) or how Windows does the same when installing feature updates, for your convenience, because it needs several reboots.
[*]Some vendors deviate from UEFI standards and made things necessarily hard for dual-booting: Whenever Windows is installed the boot order always defaults to Windows, ignoring the EFI management tools (efibootmgr) and explicit user settings. No such problem with Ubuntu alone or multi-booting Ubuntu and other Linux distros and, obviously, no such problem either with different Windows versions.
[*]At least one vendor forces users to enable a supervisor password in order to enable the options to trust and boot external installation media.
[*]You may find an unfortunate combination of #3 and #4.
[/LIST]

Secure Boot, an UEFI exclusive feature, is a red herring. It's often recommended to disable it but only because it prevents loading unsigned drivers (e.g. Nvidia). Users can keep it enabled but then must sign the drivers manually. So, knowing that Secure Boot actually isn't that secure and not so important in the grand scheme of things, better to just disable it when dual-booting with Linux. Secure Boot does NOT prevent booting installation media (read above).ç
 
So, please, familiarize yourself with *your* UEFI settings before embarking on advanced tasks and, of course, have updated and versioned backups before trying to install any other OS. 
Windows can and should be blamed for many bad things, just not for what triggered this thread. Good musicians can play their instrument no matter how flawed by understanding it and adapting the technique; bad musicians always blame the instrument. Which one do you want to be?

---

### Post by TheFu on 2021-01-07
The Linux Foundation Secure Workstation Guidelines suggest using UEFI, TPM, and Secureboot.
[https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

I use none most of the time. Only one of my systems has TPM, but it doesn't get used for other reasons.
Legacy BIOS is used because I wasn't prepared for UEFI when hardware that supported it arrived. I wasn't ready to rock the boat and don't dual-boot. When most of my virtual machines were created, UEFI support by hypervisors wasn't so good and I've just never changed.

Only a laptop uses UEFI here. I don't remember why I disabled secure boot, but think it was necessary to use a 2FA as part of the LUKS challenge/response key to unlock the system storage. I honestly don't remember.  I do recall having it enabled before with LUKS and about once a year running into problems.  That laptop never booted Windows, BTW.

---

### Post by oldfred on 2021-01-07
By removing battery, you reset fast boot to normal boot.

Fast boot is an UEFI setting that assumes no system changes and immediately boots system. No scan of hardware for changes  is done. You then have no time to press any keys to get into UEFI or UEFI boot menu. Full power down, drain all power (or remove all batteries) will have system do normal boot if you cannot get into UEFI.
Fast boot can make both Windows & Linux seem like they boot faster, if not changing anything.

Windows typically boots slow.
So they originally changed to UEFI. Required UEFI fast boot to skip check for new configuration. It has a form of hibernation called Windows fast start up in Windows that immediately loads kernel. And to speed fast start up, required vendors to add a tiny 16 to 32GB SSD to system just for the hibernated boot file(s). This was the originally Intel RST and or Intel Optane with some CPUs. Some users with the 32GB SSD, turned off Windows fast start up and used SSD just for Ubuntu's / (root). Some with larger SSD found the hibernation file was just the size of RAM, and used rest of SSD for /.  Now most systems have SSD, so separate SSD for hibernation not required, but fast start up still used.

---

