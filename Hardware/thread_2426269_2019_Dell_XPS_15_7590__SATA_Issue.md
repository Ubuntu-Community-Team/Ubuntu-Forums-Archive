---
title: "2019 Dell XPS 15 7590  SATA Issue"
date: 2019-09-06
forum: Hardware
---

### Post by makitso on 2019-09-06
Just bought the subject machine and trying to set up a dual boot 19.04 system.  The problem has to do with the BIOS setting for SATA drives:

Out of the box,  the SATA drive is configured as "SATA is configured to support RAID mode for Intel Rapid Restore."  In this mode the Ubuntu installer can not see the the non-windows partition.
I changed the SATA settings to AHCI and then dual boot installed Ubuntu.  Using gparted the windows partition is shown as Bitlocker.
However, using AHCI, when I select Windows Boot Manager from the GRUB menu the booting of Windows fails.  If I go back into BIOS and set the SATA option to RAID it will then boot but then Ubuntu fails to boot.

My questions are:

Does the Bitlocker mean my windows partition is encrypted?
Any way to configure this machine so that I can successfully boot either windows or ubuntu from the GRUG menu?

Thanks in advance

---

### Post by oldfred on 2019-09-06
Not sure about bitlocker.

But you have to install AHCI drivers into Windows before changing to AHCI.

Many Dell, even new, need UEFI update and if SSD, SSD firmware update.

       AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

Says Secure Boot & Bitlocker are related.
[https://ubuntuforums.org/showthread.php?t=2386049&p=13844034#post13844034](https://ubuntuforums.org/showthread.php?t=2386049&p=13844034#post13844034)

---

### Post by makitso on 2019-09-06
Solved it with this thread, option 1

[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)

---

