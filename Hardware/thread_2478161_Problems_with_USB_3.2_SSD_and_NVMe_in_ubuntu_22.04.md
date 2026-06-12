---
title: "Problems with USB 3.2 SSD and NVMe in ubuntu 22.04"
date: 2022-08-18
forum: Hardware
---

### Post by dohuacode on 2022-08-18
Hi to all, i met a lot of problems with Ubuntu installed on my internal NVMEe or External SSD Netac Z9 in USB 3x mode.
My laptop is HONOR MAGICBOOK PRO AMD 4600H 16 GB RAM SSD WD 512GB
[https://www.hihonor.com/global/laptops/honor-magicbook-pro/spec/](https://www.hihonor.com/global/laptops/honor-magicbook-pro/spec/)

Nvme:
Installing normally but have a lot of freezes of processes, freeze up to 2 minutes, its impossible to work that way. Freezes is mostly when a lot of read-write operations, chrome freezes, Jetbrains IDE freezers, SQL freezes all what takes resourses, telegram freezes(3 accounts with 500 channel in each), so when we need a lot of read-write - freeze. Telegram is crashing at all.

EXTERNAL SSD in USB 3x mode:
Same problem but worse, problem starts even in installation, installer cant create ext4 patition, but gparted some times can, sometimes not.
OK partitioned in gparted and installed. So its same problem like NVMe but more. Processes freezes up to 10 minutes, or forever, so you have to kill them. And then freezes all system at all.

So solution with external SSD is dowgrade to USB 2x with old USB hub,  system installs, everything works fine, yes freezes is present, but they very short, overall perfomance on USB 2x mode is lower, but processes woks stable way, i can freeze but on 1-2 seconds maximum, Telegram works fine too with all 1500+ channels.
If to install Ubuntu on old external USB HDD 5200RPM - so it works fine too
Tried Ubuntu,Kubunty,Xubuntu

---

### Post by oldfred on 2022-08-18
Strange that USB2 works and USB3 does not as USB3 has been more standard for years.
I converted to only using USB3 flash drives years ago, mostly for full installs.
And recently converted my desktop's M.2 SATA drive to NVMe drive and moved SATA drive to a M.2/USB3 adapter. That has really worked well for me.

Do you have internal install to check logs for errors?

I do not know AMD, but have seen were many AMD systems needed boot parameters or UEFI settings on iommu or other boot parameters.
Do you have an IOMMU setting in UEFI, or something related?

Many systems have also need UEFI firmware updates & NVMe firmware updates. Do you have most recent firmware?
To see NVMe firmware version to compare to vendors site.
udisksctl status
or 
sudo apt install nvme-cli
sudo nvme list

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dohuacode on 2022-08-19
> **oldfred said:**
> Strange that USB2 works and USB3 does not as USB3 has been more standard for years.
I converted to only using USB3 flash drives years ago, mostly for full installs.
And recently converted my desktop's M.2 SATA drive to NVMe drive and moved SATA drive to a M.2/USB3 adapter. That has really worked well for me.

Do you have internal install to check logs for errors?

I do not know AMD, but have seen were many AMD systems needed boot parameters or UEFI settings on iommu or other boot parameters.
Do you have an IOMMU setting in UEFI, or something related?

Many systems have also need UEFI firmware updates & NVMe firmware updates. Do you have most recent firmware?
To see NVMe firmware version to compare to vendors site.
udisksctl status
or 
sudo apt install nvme-cli
sudo nvme list

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for reply, here is my
 boot  report from my SSD in USB 2.0 mode, i cant see anything special : 
[https://paste.ubuntu.com/p/kBKd6nkwxY/](https://paste.ubuntu.com/p/kBKd6nkwxY/)
Only stange it says that boot/efi on sda3, i can see grub folders on EFI partition, and on sda3 partition too
I dont tried to boot in usb 3 mode, afraid of total crash, and reinstall of system.

About NVMe version i will try to look for firmware updates, but now i have Windows on NVME, Ubuntu only on SSD, Netac is cheap vendor, so i cant find any normal tools for firmware update.

Bios is very pour in my laptop, all interesting what  i can do is disable SecureBoot, now its disabled.
And disable TPM, now disabled.
NO IOMMU of something else
Of course i tried installations to SSD in usb 3 mode with this options turned on and off - no difference, same problems

---

### Post by tea for one on 2022-08-19
You have:-
[COLOR="#0000FF"]Line 7[/COLOR] - sda1 - bios boot partition
[COLOR="#0000FF"]Line 13[/COLOR] - sda2 EFI system partition

This indicates that you booted the usb installer in Legacy mode.
However, this does not explain the problems mentioned in your original post.

If you have a backup, I would seriously consider re-installing in UEFI mode only i.e. bios boot partition would not be installed.

---

### Post by dohuacode on 2022-08-19
I created bios partition myself because i wanted portable linux, which works on all machines, but it all are details, it do not cause current problem, because i of course tried installation without bios partition, i suppose its about bad support of amd north bridge in ubuntu....because problem has a place both on nvme and ssd

---

### Post by oldfred on 2022-08-19
A bios_grub partition has to be unformatted and only needs to be 1 or 2MB. It cannot be NTFS.
With no grub in MBR, the bios_grub is not used.

You do have UEFI boot.

As long as you have Windows you can have a NTFS partition. It may need chkdsk, defrag or other repairs that you only can do from Windows.
Check that Windows fast start up is off, or that prevents normal mount of a NTFS partition.

Some parameters for NTFS.
Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)

You might test a iommu setting in grub as you boot.
[https://ubuntuforums.org/showthread.php?t=2347115](https://ubuntuforums.org/showthread.php?t=2347115)

---

### Post by dohuacode on 2022-08-20
> **oldfred said:**
> A bios_grub partition has to be unformatted and only needs to be 1 or 2MB. It cannot be NTFS.
With no grub in MBR, the bios_grub is not used.

You do have UEFI boot.

As long as you have Windows you can have a NTFS partition. It may need chkdsk, defrag or other repairs that you only can do from Windows.
Check that Windows fast start up is off, or that prevents normal mount of a NTFS partition.

Some parameters for NTFS.
Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)

You might test a iommu setting in grub as you boot.
[https://ubuntuforums.org/showthread.php?t=2347115](https://ubuntuforums.org/showthread.php?t=2347115)


I dont have IOMMU setting in bios.
No windows in parralel with Ubuntu, just NTFS partiton,  i turning of NVME when using Ubuntu from USB.
In windows hibernate and fastboot is turned off when i use windows

---

