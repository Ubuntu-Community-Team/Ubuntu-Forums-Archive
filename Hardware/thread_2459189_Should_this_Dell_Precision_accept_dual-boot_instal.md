---
title: "Should this Dell Precision accept dual-boot installation easily?"
date: 2021-03-12
forum: Hardware
---

### Post by Richard_York on 2021-03-12
I've found a Dell Precision (spec below) refurbished online.
Last year I bought an Asus which I'm going to sell on at a loss - it fought against Ubuntu installation, and in my ignorance I hadn't realised how limiting a fairly early i3 processor would be. Other issues too, though it works perfectly on Windows.

Before I get financially burned again, if this Dell machine stays available long enough, would you recommend it as suitable for dual-boot installing alongside its Windows10 with Ubuntu 20.04?

I am no expert, but have installed dual boot with earlier Ubuntu editions on other laptops. The Asus defeated me, my ability is limited to fairly straightforward installations.

With thanks.

> [FONT=arial]Processor - Intel Core i7-2820QM 2.30GHz Quad Core (3.40GHz Max Turbo Frequency, 8MB Intel Smart Cache)[/FONT] 
[COLOR=#000000][FONT=Arial]     [FONT=arial]Graphics - Nvidia Quadro 3000M 2GB GDDR5 Discrete[/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]Display - 17.3" LED backlit FHD Anti-Glare UltraSharp[/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]Display Resolution - 1920 x 1080[/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]Hard Drive - 500GB SATAIII [/FONT][FONT=arial]([/FONT][FONT=arial][COLOR=#222222]Support for one or two 2.5" storage devices[/COLOR][COLOR=#222222])[/COLOR][/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]RAM - 8GB DDR3 SDRAM (4 Slots, Max 32GB) [/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]LAN - Gigabit Ethernet 10/100/1000[/FONT] 
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial]     [FONT=arial]Audio - [/FONT][FONT=arial][COLOR=#222222]Dual integrated high quality speakers and dual integrated noise cancelling digital array microphones[/COLOR][/FONT] 
[/FONT][/COLOR]
[FONT=arial]Optical Drive - DVD-RW[/FONT]  [COLOR=#000000][FONT=Arial]     [FONT=arial]Keyboard - UK Language with Numeric Keypad[/FONT] 
[/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial]  
[/FONT][/COLOR]

---

### Post by grahammechanical on 2021-03-12
I am not am expert but I do not see anything in the specification of that machine that would prevent Ubuntu from running on it. It is now old technology. Linux should have the hardware drivers for this technology. Nvidia even has a video driver for Linux. I would be surprised if Ubuntu was not able to install this driver.

[https://www.nvidia.com/download/driverResults.aspx/95159/en](https://www.nvidia.com/download/driverResults.aspx/95159/en)

Where else would there be problems? You, yourself said it.

> it fought against ubuntu installation

You do not describe the form that this resistance took. No installation of a Linux distribution is straightforward when any version of Windows is pre-installed. A lot will depend on if the manufacturer has made it difficult to make changes to the UEFI settings. And there is a certain procedure that must be followed. This page is old but I do believe it is still relevant:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by Richard_York on 2021-03-13
Thanks, that's helpful. I didn't describe the Asus problems to save space - I should have included this link:  [https://ubuntuforums.org/showthread.php?t=2457675](https://ubuntuforums.org/showthread.php?t=2457675)     where a work-round was offered, though it would stretch my competence level.
By then other issues with the machine had persuaded me it was the wrong laptop for me.

I'm hoping to find something where work-rounds and fixes aren't needed, or at least, only minor ones. When I first posted last year with problems installing, one reply was along the lines of "I wouldn't have bought that machine, it won't do what you want" so I'm trying not to replicate this!
.

---

### Post by iamjiwjr on 2021-03-13
I have a new Precision desktop. It came with Ubuntu pre-installed. I've installed 6 or 8 other distros that do well too. I've never dual-booted (I'm retired now so I am liberated from the Win thing), but, if it will install one, two shouldn't be an issue. Hopefully yours should work well. I have a 2010 Dell Inspiron laptop and had in the past a 2015 Inspiron desktop. Both of them dual-booted fine with Linux and the Win thing.

---

### Post by Richard_York on 2021-03-13
Thanks for these replies. I didn't buy that one, but another Dell, with i7 and SSD, and hope I don't end up asking for too much help here when I come to install Ubuntu on it!

---

### Post by oldfred on 2021-03-13
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Be sure to create Ubuntu live installer in UEFI mode if using Rufus. Most tools create installer that can be booted in either UEFI or BIOS, but then you have to choose UEFI boot of live installer in UEFI boot menu (f12).

General UEFI install instructions in link below in my signature.

---

### Post by Richard_York on 2021-03-17
Thank you, OldFred, you've anticipated the questions I'd be asking next !
I'll mark this thread solved, and if new issues arise will post more specifically.

---

