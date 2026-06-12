---
title: "Cloned 970 EVO will not boot Ubuntu 20.04"
date: 2020-12-25
forum: Hardware
---

### Post by jnmjr on 2020-12-25
Hello all, I got this new Lenovo Legion 5i 17" laptop cause I want to  retire my desktop. Cloned my existing 860 Evo ssd 2.5 to a new 970 Evo  NVMe. Installed by itself in first slot after removing the win10 ssd.  The drive is seen in the bios but will not boot " Ubuntu 970 Evo boot  failed".
Grub is installed in boot partition as it should, tried Boot  Repair to no avail, Secure Boot is disabled in bios, searched for  solutions, tried what I found, nothing works, I formatted the new ssd  and installed fresh Ubuntu 20.04, it works flawlessly in Lenovo. I dd  cloned again to try in another laptop, LG Gram 2020, it worked fine, put  drive back in Lenovo, boot fail????  I'm  stubborn and want this to work because it seems to be a Lenovo issue, I  have done this dd cloning before desktop to desktop without issues,  first time to a laptop, I want to stress I use the Terminal only when I  have no choice and always copying and pasting from online solutions as  I'm not a command line guy. I hope some of you can suggest a working  solution to this issue. Thank you.

PS: BTW it only takes me 15 mins. to clone the ssd.

---

### Post by oldfred on 2020-12-25
I believe in new installs to avoid issues.

Have you updated UEFI and SSD firmware. 
With my Samsung NVMe drive I had to download the bootable ISO to run the update. I do not have Windows, but was able to boot ISO and update NVMe to latest firmware.

Is drive in UEFI set to AHCI mode? 
What video does that system have? It may need drivers, depending one video hardware.

Is cloned drive UEFI?
You have to to boot drive setting like you do with flash drive installer as UEFI will not have an "ubuntu" entry until you manually add one with efibootmgr or reinstall grub.

---

### Post by TheFu on 2020-12-25
Interesting.  I received a 970 EVO this morning. Planned to clone a Micron 1150 (SATA-SSD) into it tomorrow and see how it boots.  That system doesn't use EFI booting.  I'd read a number of places that changing from SATA to NVMe wasn't possible using a straight clone (dd/ddrescue) technique - be 100% certain to clone only from alternate boot media.
[https://www.reddit.com/r/debian/comments/hrmskg/migration_from_sata_ssd_to_nvme_ssd/](https://www.reddit.com/r/debian/comments/hrmskg/migration_from_sata_ssd_to_nvme_ssd/)

Since I use LVM, a pvmove should work, regardless. Hummm. Are you using LVM?

I'm not really thrilled trying to migrate all the existing stuff from the Micron over to the 970 even for a 4x speed improvement. It is hosting a bunch of VMs and LXD containers, each with a separate backup/restore process.  That pvmove method is looking better and better now. I have used it before.

If either cloning or pvmove fail, I know my normal storage failure restore method will work, but it begins with a fresh, minimal, Ubuntu Server install. Sure it is just 30 minutes to get the hostOS back the way it was, in theory, but the NVMe added wrinkle has me a little concerned.

I think boot-repair hasn't really worked in years for UEFI boot needs.  Really just use that for gathering data, not actually to fix anything if EFI is involved.  Boot-repair probably does work with a single-HDD, Legacy BIOS boot setup still.

Does NVMe support AHCI? I thought NVMe was PCIe, thus not connected to SATA nor AHCI at all.  A little googling says that only certain NVMe storage supports AHCI modes and only certain NVMe m.2 slots on MBs support it too.  I know my B450 motherboard has 2 m.2 slots, each with specific capabilities.  1 Supports SATA m.2 or NVMe.  The other supports NVMe only, no SATA. There are some unexpected rules about which storage devices can be connected to which m.2 slots and under which situations. I remember being surprised when I first learned of these restrictions and knew that I'd have to lookup the details before any changes, each time.   It is sorta like how only specific RAM slots can be used, but more complex.

---

### Post by oldfred on 2020-12-25
I do not use LVM, and upgraded M.2 SATA to larger NVMe SATA on Z170, Intel based system. Built in 2016 when NVMe was expensive so used the SATA drive, but wanted to try NVMe, since now less expensive. Put M.2 SATA into an USB adapter and have very fast external drive.
Did new UEFI install to gpt drive and copied my data partition from HDD to NVMe drive. 

I do not think I changed any UEFI settings, and drives are all in AHCI mode. 
This shows revision number & I had older version of firmware. Found Samsung had ISO with newer firmware and it was actually bootable with grub2's loopmount.
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list


Arch as usual has some good info on NVMe drives.
[https://wiki.archlinux.org/index.php/Solid_state_drive/NVMe](https://wiki.archlinux.org/index.php/Solid_state_drive/NVMe)

---

### Post by jnmjr on 2020-12-25
> **oldfred said:**
> I believe in new installs to avoid issues.

Have you updated UEFI and SSD firmware. 
With my Samsung NVMe drive I had to download the bootable ISO to run the update. I do not have Windows, but was able to boot ISO and update NVMe to latest firmware.

Is drive in UEFI set to AHCI mode? 
What video does that system have? It may need drivers, depending one video hardware.

Is cloned drive UEFI?
You have to to boot drive setting like you do with flash drive installer as UEFI will not have an "ubuntu" entry until you manually add one with efibootmgr or reinstall grub.

Thank you for your post,

1) Since it works with fresh install, my guess is no updates needed. Clone works in Lg Gram 2020 no issue.

2) Yes....... the Lenovo  Nvidia Gforce GTX 1660ti, desktop Gforce GTX 1050ti. I wouldn't know how to load drivers since it doesn't boot at all. LG laptop no Nvidia  but it booted fine?

3) Yes 

I strongly agree with your opening remark, but it would make it so much easier to keep all my settings and programs.

---

### Post by jnmjr on 2020-12-25
> **TheFu said:**
> Interesting.  I received a 970 EVO this morning. Planned to clone a Micron 1150 (SATA-SSD) into it tomorrow and see how it boots.  That system doesn't use EFI booting.  I'd read a number of places that changing from SATA to NVMe wasn't possible using a straight clone (dd/ddrescue) technique - be 100% certain to clone only from alternate boot media.
[https://www.reddit.com/r/debian/comments/hrmskg/migration_from_sata_ssd_to_nvme_ssd/](https://www.reddit.com/r/debian/comments/hrmskg/migration_from_sata_ssd_to_nvme_ssd/)

Since I use LVM, a pvmove should work, regardless. Hummm. Are you using LVM?

I'm not really thrilled trying to migrate all the existing stuff from the Micron over to the 970 even for a 4x speed improvement. It is hosting a bunch of VMs and LXD containers, each with a separate backup/restore process.  That pvmove method is looking better and better now. I have used it before.

If either cloning or pvmove fail, I know my normal storage failure restore method will work, but it begins with a fresh, minimal, Ubuntu Server install. Sure it is just 30 minutes to get the hostOS back the way it was, in theory, but the NVMe added wrinkle has me a little concerned.

I think boot-repair hasn't really worked in years for UEFI boot needs.  Really just use that for gathering data, not actually to fix anything if EFI is involved.  Boot-repair probably does work with a single-HDD, Legacy BIOS boot setup still.

Does NVMe support AHCI? I thought NVMe was PCIe, thus not connected to SATA nor AHCI at all.  A little googling says that only certain NVMe storage supports AHCI modes and only certain NVMe m.2 slots on MBs support it too.  I know my B450 motherboard has 2 m.2 slots, each with specific capabilities.  1 Supports SATA m.2 or NVMe.  The other supports NVMe only, no SATA. There are some unexpected rules about which storage devices can be connected to which m.2 slots and under which situations. I remember being surprised when I first learned of these restrictions and knew that I'd have to lookup the details before any changes, each time.   It is sorta like how only specific RAM slots can be used, but more complex.

Thank you for your post,

Neither clone nor fresh install use LVM. AHCI is enabled in bios automatically no option to turn it off, machine came with a NVMe ssd Win10. As far as I know it doesn't interfere with NVMe.

---

### Post by oldfred on 2020-12-25
I will let TheFu really chime in on backups.
Your backups should enable you to fully restore your system and do not need to be really complicated. All your user settings are in /home and you need a list of installed apps. Then maybe /etc, if reinstalling same version, but new version may have some settings different so backup should not be totally restored. If server or other applications that get installed in / (root) like database or web, you would need to back those up, but if running a server I expect you to know those applications & how to back them up.

One advantage of a new drive and restore from your normal backup is that you then can be confident that when your drive fails & you have to restore from backup, you have everything you need. But with old install, you can still add anything missing from backup.

Almost all systems need UEFI firmware updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. And even new systems often get UEFI updates for various fixes.

Nvidia systems used to always need nomodeset to boot, both live installer & first boot or until nVidia driver installed. New installs now have option to install nVidia driver as part of install.
But driver version has to match hardware. Some older hardware uses the older drivers which may not work or fully work on newer video cards/chips.

---

### Post by oldfred on 2020-12-25
Boot-Repair works just about as well with UEFI as BIOS.
Its just that it is a gui front end to reinstalling grub or updating grub menu.
I like it for its Summary report which then can show details of install and perhaps other issue.
It now seems to also run fsck, but only automounts standard partitions, / , /boot & ESP. So is user has separate /var or other system folders as partitions, it does not by default mount those and repair will not work. Or it works best on simple desktop installs which most newer users that want gui help use.

With BIOS, it could install syslinux MBR boot loader to allow fix to Windows boot, but cannot fix Windows UEFI boot.

---

### Post by jnmjr on 2020-12-25
I want to thank you fellows for your input it has been very educational, in truth I don't want to fool around with this issue any more, a backup will do most of what I need and I'll manually do the rest.

---

