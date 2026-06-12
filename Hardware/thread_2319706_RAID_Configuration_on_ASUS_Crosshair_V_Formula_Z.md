---
title: "RAID Configuration on ASUS Crosshair V Formula Z"
date: 2016-04-06
forum: Hardware
---

### Post by tonysonney on 2016-04-06
Hello All,
         I am trying to build a PC with RAID configuration. The main configurations are

Motherboard       *Criosshair V Formula Z*
CPU                   *FX9590*
SSD                   *5x 120GB Sandisk SSD Connected on Sata port 1-5*

     I have set
Port1-4                                        *RAID*
Port5-6                                        *RAID*
Board SATA RAID ROM                    [I]Legacy ROM
[/I]
Within the AMD ROM Utility, have set the RAID array to use RAID mode 5 with all the SSDs totalling 507.99GB. When I restart the BIOS detects it as one drive 'Logical Drive 1'

_Problem_
      When I try to install ubuntu on the RAID. Ubuntu detects the storage as  5 drives of 120GB sda-sde, as if the BIOS RAID configuration never existed. I would have expected the RAID controller to present the memory as 1 single chunk of 507GB. 

- Can somebody please help? Am I missing any configuration?

- Is it safe to assume "Crosshair V Formula Z" has actual "hardware" RAID controller and not the fake controller which relies on OS to perform RAID read/writes? It has SB950 controller and all the tools I can find supports Windows only.

Many Thanks,
Tony

---

### Post by frostschutz on 2016-04-08
Is this Linux only or a dual boot Linux+Windows box where both OS have to share the same RAID?

For Linux only, it would be best to ignore whatever RAID options the BIOS offers, and use Linux native software RAID (mdadm).

> actual "hardware" RAID controller

only exists as cards, never onboard, unless perhaps specialized server boards enterprise hardware I don't know about.

even many cards are fakeraid only...

doesn't matter either way since hardware raid really sucks

---

### Post by tonysonney on 2016-04-08
It will be an Linux only machine :) . 

I have been trying to use the mdadm to use Software raid. But every time ubuntu installations fails on grub install. Even though I asked the installer to install bootloader on sdg, it tries to install it on sda which is one of the raid harddisk and failed. Once the grub install fails it crash the installer. I will try the server installer which might let me do the grub install manually.

---

### Post by frostschutz on 2016-04-08
It should be possible for the bootloader to be on the RAID disks (all of them so booting still works regardless which disk dies). Not sure what went wrong when you tried it; are you using whole disks for RAID? You should only use partitions to avoid problems with all sorts of things.

A partition table is the most commonly understood way to declare that a disk is in use and by what; so every disk should have a partition table regardless what you do with it, or risk that installers, bootloaders, partitioners etc. misinterpret things.

With software raid you are not restricted to a single raid level for the whole disk, you can combine them. So you can have a RAID-1 /boot partition (RAID-1 over all disks, using 0.90 or 1.0 metadata) which works even for bootloaders that are not RAID-aware; and a RAID-5, RAID-6, RAID-10 (whatever you fancy) /, /home, /data or whatnot partition for the rest of the disks...

---

### Post by tonysonney on 2016-04-11
The problem I have are mainly.

_Using Ubuntu 14.04.4 "Desktop" Installer"_
grub-update failed to install on /dev/sda

At this point, ubuntu installer crash and gives up.

_Using Ubuntu 14.04.4 "Server" Installer_
It installs fine. It gives me a shell to install grub. [ The installer does the grub install on both /dev/sda to sde].  But on reboot, it fails with following error.
*error: disk 'mduuid/<32 digit hex number>,1' not found.*
Entering rescue mode>

---

### Post by tonysonney on 2016-04-12
I think the problem is mdadm stores the UUID of the raid device somewhere. Once the ubuntu installtion is done the UUID is changed. Is there a way to force mdadm to update UUID? I tried modifying /etc/mdadm/mdadm.conf. But mdadm still reads the old UUID.

---

