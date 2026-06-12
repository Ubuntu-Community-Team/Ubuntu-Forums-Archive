---
title: "Boot Drive not found on HP Elitebook 850G2"
date: 2022-03-06
forum: Hardware
---

### Post by chribonn on 2022-03-06
[FONT=arial][COLOR=#232629]I am trying to install Ubuntu on an HP Elitebook 850G2. I boot from USB and the installation appears to go flawlessly.

[/COLOR]
[COLOR=#232629]When the laptop boots after installation the boot drive is not recognised.

[/COLOR]
[COLOR=#232629]I tried using both Server 20.04.3 and Desktop 21.10.[/COLOR]
[COLOR=#232629]
Laptop is on the latest HP BIOS. These is not other OS installed on the computer.[/COLOR]
[COLOR=#232629]
If I load Ubuntu from the USB (Live CD) on the laptop it load OK.

What could I do / try to diagnose and solve the problem?[/COLOR][/FONT]

---

### Post by oldfred on 2022-03-07
Not that you need any repair, the report will just confirm your configuration.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

HP often only lets users change boot order from within UEFI settings (not the UEFI boot menu), grub uses efibootmgr which every other system seems to accept.
Can you boot Ubuntu from UEFI boot menu?

Not sure if similar to this?
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

---

### Post by chribonn on 2022-03-09
Pastebin link: [http://paste.ubuntu.com/p/dsZ8d2sn54](http://paste.ubuntu.com/p/dsZ8d2sn54)

Thanks

---

### Post by mIk3_08 on 2022-03-09
> **chribonn said:**
> [FONT=arial][COLOR=#232629]I am trying to install Ubuntu on an HP Elitebook 850G2. I boot from USB and the installation appears to go flawlessly.[/COLOR]
[COLOR=#232629]When the laptop boots after installation the boot drive is not recognised.[/COLOR]
[COLOR=#232629]I tried using both Server 20.04.3 and Desktop 21.10.[/COLOR][COLOR=#232629]
Laptop is on the latest HP BIOS. These is not other OS installed on the computer.[/COLOR][COLOR=#232629]
If I load Ubuntu from the USB (Live CD) on the laptop it load OK.
What could I do / try to diagnose and solve the problem?[/COLOR][/FONT]
I think you should read this, [Click here]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS") for more info. Maybe this will help you solve your issue. Good luck and Cheers

---

### Post by tea for one on 2022-03-09
[COLOR="#0000FF"]Lines 17 - 29[/COLOR] - You have a Bios boot partition and an EFI partition.
Probably why Grub is a bit confused?

As this is a recent installation, I would suggest that you start from scratch to make the system more future proof.

Back up any personal data
Boot into a live session in [COLOR="#0000FF"]UEFI[/COLOR] mode (how you boot determines the installation mode)
Double check that the disk is still GPT via gparted.
Allow the installer to automatically create the necessary partitions (or your preferred configuration)

I reckon that you'll be up and running in less than an hour ;).

---

### Post by oldfred on 2022-03-09
How you boot install or repair media is how it installs or repairs.
You have UEFI system & UEFI install, but have made BIOS install or repairs which installed grub to gpt's protective MBR & created a bios_grub partition.
But you have the mount of the ESP - efi system partition in fstab, so install is UEFI.
It should boot from UEFI boot menu, but since only Ubuntu you normally will not get grub menu. When booting in UEFI mode, you have to use escape key just after vendor logo, but before grub menu normally shows to get grub menu. If UEFI fast boot is on, you may not have any time with a "warm" reboot, but a full power down "cold" boot may give you just enough time to press escape.

HP is one that seems to want to boot "Windows Boot Manager" by description. It does not actually check what boot file is actually used. So those with only Ubuntu can create a new UEFI boot entry that says Windows, but boots using shim.

From live installer, booted in UEFI mode.
    sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
(above is buried somewhere in the link below in my signature.)

---

### Post by chribonn on 2022-03-10
> **tea for one said:**
> [COLOR=#0000FF]Lines 17 - 29[/COLOR] - You have a Bios boot partition and an EFI partition.
Probably why Grub is a bit confused?

As this is a recent installation, I would suggest that you start from scratch to make the system more future proof.

Back up any personal data
Boot into a live session in [COLOR=#0000FF]UEFI[/COLOR] mode (how you boot determines the installation mode)
Double check that the disk is still GPT via gparted.
Allow the installer to automatically create the necessary partitions (or your preferred configuration)

I reckon that you'll be up and running in less than an hour ;).

Thank you for the tips.

This is a freshly formatted laptop with no data.

I logged in the HP's BIOS and reset to defaults.

I will follow your advice and report back.  It **could** be that my USB was not configured to boot in UEFI.

---

### Post by tea for one on 2022-03-10
> **chribonn said:**
> It **could** be that my USB was not configured to boot in UEFI.

Have a look at the UEFI Set Up pages on your PC and see if there is an option to [COLOR="#0000FF"]Disable Legacy Mode[/COLOR] or similar phrase.
If Legacy mode is disabled, then your USB installer will automatically boot in UEFI mode.

---

### Post by chribonn on 2022-03-10
It was that.  In the BIOS I set the setting with EUFI wtihout CMS and I set Rufus to format the USB to the equivalents. 

Laptop booted.

Thanks you very much.

---

