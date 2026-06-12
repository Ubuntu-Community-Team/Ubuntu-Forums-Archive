---
title: "Trying to launch Windows7 from an NVME via Grub. &quot;Device not found&quot;. Help."
date: 2018-10-06
forum: Hardware
---

### Post by Mugsy323 on 2018-10-06
Okay, I confess I'm trying to do something unusual. I need a Grub expert. ;)

*(yes, I know this isn't a Windows support forum. I need help with Grub.)*

My old Win7 PC doesn't have nvme sockets so I bought an x4 adapter card to connect a 500GB 970 Evo.

I've installed the Evo & cloned my C: (Windows/boot) drive to it. I then unplugged C: and booted to the Grub boot menu (dual-boot PC with Ubuntu 18.04.1 LTS.)

From the recovery mode, I updated the boot loader to update the OS list. It found Windows on the nvme (yea!) :grin:

But when I select it from Grub, it (grub) immediately reports "Device not found". WTH? :???:

Is there a way around this?

---

### Post by oldfred on 2018-10-06
Using adapter cards can work and then again may not work. 

Does Windows 7 even work from NVMe?

Boot-Repair uses bootinfoscript as part of report. But it has not been updated to include NVMe devices. So report helps but is not complete.
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
I do not have NVMe drive, and author want someone who does to help update script.
       Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)

---

### Post by Mugsy323 on 2018-10-06
> **oldfred said:**
> Using adapter cards can work and then again may not work. 

Does Windows 7 even work from NVMe?

Boot-Repair uses bootinfoscript as part of report. But it has not been updated to include NVMe devices. So report helps but is not complete.
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
I do not have NVMe drive, and author want someone who does to help update script.
       Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)

Thanks for the reply. MS released a Hotfix to add support for NVMe drives to Win7 w/SP1. After running the hotfix and rebooting, the Computer Manager detected the drive and let me format it. Mine is installed, formatted and I can read/write to it like any other drive.

I've found **[a website]("https://www.win-raid.com/t2375f50-Guide-NVMe-boot-without-modding-your-UEFI-BIOS-Clover-EFI-bootloader-method.html")** with utility that (supposedly) shows you how to load Win7 off an NVMe by booting from a USB boot drive, but I downloaded their utility and it doesn't seem to work (it formats a USB flash drive and is then supposed to copy files to it. It formats, but no files are created. Even tried running as Admin.)

I'd much prefer to use the existing Grub boot menu anyway, but that may not be possible w/o loading some sort of "device handler" first. :)

---

### Post by Mugsy323 on 2018-10-08
Is there a way to edit Grub so that it is able to locate the drive it says is "not found"?

As noted in my original question, I booted into Recovery Mode and selected the option to automatically "Update Grub". It found Windows on the nvme drive, yet for some reason, can't find the drive when I'm on the Grub boot menu. :?

Might there be a way to edit Grub (or whatever data files it relies on) so it can find the nvme to boot from it?

---

### Post by oldfred on 2018-10-08
Did you run the Summary report from Boot-Repair? Just post link.
Need to see details.

---

### Post by Mugsy323 on 2018-10-09
I hadn't heard of "Boot-Repair". I installed it and created a Summary report (note: Windows *was* on "/dev/sdb" but now resides on "/dev/nvme0n1p1".)

I uploaded the report **[here]("https://mega.nz/#!6V0SDIgY!mMR6bUmvE1gws-NarDeZfte3bca9TR-ZBOn-xGoD7aA")**.

TIA

---

### Post by oldfred on 2018-10-09
Boot-Repair uses bootinfoscript for part of its report & that has not been updated to show NVMe drives. So do not see Boot files in NVMe drive.
Grub's os-prober thinks it is Vista? Was this an upgrade from a Vista install, so something there that makes it think it is Vista?
But I do not think boot stanza in grub is different. And it refers to the correct UUID for your /dev/nvme0n1p1. 

Does Windows correctly boot from BIOS?
Grub only boots working Windows, so Windows cannot be hibernated nor need chkdsk. 
And newer Windows 8 or 10's fast start up is always on hibernation that must be turned off.

I have seen this the insmod is add in drivers for grub, many already are loader, but to be sure:
       alternate to chainloader +1
      
 insmod ntldr 
    ntldr /bootmgr  

    
The os-prober is using the chainload type entry. You could copy into 40_custom and change chain line to the ntldr line.

---

### Post by QIII on 2018-10-09
I'm going to echo oldfred in asking whether you can boot to Windows successfully.

Not all motherboards support booting from NVMe and not all adapters provide such support, which requires specific firmware.  Even with the appropriate firmware, the motherboard still may not boot.

---

### Post by Mugsy323 on 2018-10-09
> **oldfred said:**
> Boot-Repair uses bootinfoscript for part of its report & that has not been updated to show NVMe drives. So do not see Boot files in NVMe drive.
Grub's os-prober thinks it is Vista? Was this an upgrade from a Vista install, so something there that makes it think it is Vista?
But I do not think boot stanza in grub is different. And it refers to the correct UUID for your /dev/nvme0n1p1. 

Does Windows correctly boot from BIOS?
Grub only boots working Windows, so Windows cannot be hibernated nor need chkdsk. 
And newer Windows 8 or 10's fast start up is always on hibernation that must be turned off.
Thanks for the reply. I have Windows-7 installed on a Sata SSD. I didn't upgrade from Vista, but Grub has always (mis)identified Windows-7 as "Vista". I don't know why. I've always assumed there was just no way to tell the two apart just from the boot info.

What I did: I cloned my working Win7 install (including "System Reserved" partition) to the M.2 then disconnected the Sata SSD C: boot drive. I have Ubuntu on a different SSD.

When I boot my computer, with no other boot drive present, it defaults to my Linux drive and loads Grub.

I then went into "Recovery Mode" from Grub and selected the option to scan/update OS's. It finds Windows on the M.2 and updates Grub accordingly. But when I reboot and select "Windows (/dev/nvme0n1p1)" from the menu, Grub immediately responds "Device not found".

I don't know if it matters or not, but "/dev/nvme0n1p1" is the "System Reserved" partition. The Windows files & folders are actually on "/dev/nvme0n1p2".

As noted, my old computer does not support booting from a PCIe device (which is why I'm hoping Grub can launch it instead) and predates M.2 cards. Windows-7 itself is updated to detect the M.2 so I can read/write to it like any other disk.

Grub obviously can SEE the M.2 when it *updates* Grub, so why does it report "Device not found" when I try to boot from it?

> **oldfred said:**
> 
I have seen this the insmod is add in drivers for grub, many already are loader, but to be sure:
       alternate to chainloader +1
      
 insmod ntldr 
    ntldr /bootmgr  

    
The os-prober is using the chainload type entry. You could copy into 40_custom and change chain line to the ntldr line.
I'm afraid I have no idea what to do with that information. :redface:

Thanks.

---

### Post by oldfred on 2018-10-09
Your system reserved may be the boot partition.
Vista normally had only one NTFS partition, but Windows 7 installed using a small Boot partition and then the main install.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

So Windows will not boot on its own. 
That could be a Windows issue, or clone is not quite correct.
Do you see the 3 Windows boot files in the NVMe partitions.

You are going to copy just the Windows boot stanza from grub to 40_custom. Then add the insmod command  near top & change/delete chainload line and add bootmgr line as above.
      
 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy Windows boot stanza and edit :
sudo -H gedit /etc/grub.d/40_custom
or
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by Mugsy323 on 2018-10-11
> **oldfred said:**
> Your system reserved may be the boot partition.
Do you see the 3 Windows boot files in the NVMe partitions.

You are going to copy just the Windows boot stanza from grub to 40_custom. Then add the insmod command  near top & change/delete chainload line and add bootmgr line as above.
      
 Copy the  entries from this:
Sorry for the late reply.

I started to experience computer problems due to repeated unplugging/plugging my Windows SSD and pointing Linux to different drives for files, due to trying to setup the NVMe to boot. I never got a chance to try out your suggestion and I'm extremely curious to know if it'll work, but for the time being, I think I need to leave my hardware alone for a few days before I screw something up (again.) :P

Thanks.

---

