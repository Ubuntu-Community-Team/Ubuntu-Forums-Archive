---
title: "Hardware Problem (Need Verification)"
date: 2008-06-29
forum: Hardware
---

### Post by elwin_windleaf on 2008-06-29
I recently built a new system and loaded Kubuntu and Ubuntu (8.04) on it. The install went just fine, but afterwards the computer did one of two things:

1. Froze solid under Kubuntu
2. Logged me out of my session under Ubuntu

Somewhere through this process, I noticed that "Kernel Panics" were being thrown.

I believe it might be the motherboard I chose - I'm using a Gigabyte GA-MA790X-DS4. I was able to test the rest of the components, and they didn't seem to be causing the problems. The whole machine runs quite stable under Windows, but I would much rather run Ubuntu.

If anyone has any suggestions as to what I can do (replacement motherboard suggestions would be welcome, but I'd rather use the one I've got), I'd appreciate it!

Here are the rest of the specs, in case they help.

- Seagate SATA 500 GB data drive, WD Raptor 36GB SATA System drive
- nVidia GeForce 8800 GS
- AMD Phenom 9600 2.3 GHz Processor
- 2GB DDR2 1066 RAM

Note: If I can be sure it's my motherboard that's causing the problem, I'll add it to the Hardware Incompatibility thread.

---

### Post by chewearn on 2008-06-30
Can you post the exact kernel panic messages, some one might have a clue.

---

### Post by ukripper on 2008-06-30
> **elwin_windleaf said:**
> I recently built a new system and loaded Kubuntu and Ubuntu (8.04) on it. The install went just fine, but afterwards the computer did one of two things:

1. Froze solid under Kubuntu
2. Logged me out of my session under Ubuntu

Somewhere through this process, I noticed that "Kernel Panics" were being thrown.

I believe it might be the motherboard I chose - I'm using a Gigabyte GA-MA790X-DS4. I was able to test the rest of the components, and they didn't seem to be causing the problems. The whole machine runs quite stable under Windows, but I would much rather run Ubuntu.

If anyone has any suggestions as to what I can do (replacement motherboard suggestions would be welcome, but I'd rather use the one I've got), I'd appreciate it!

Here are the rest of the specs, in case they help.

- Seagate SATA 500 GB data drive, WD Raptor 36GB SATA System drive
- nVidia GeForce 8800 GS
- AMD Phenom 9600 2.3 GHz Processor
- 2GB DDR2 1066 RAM

Note: If I can be sure it's my motherboard that's causing the problem, I'll add it to the Hardware Incompatibility thread.

Can you post output of the following when you manage to boot into ubuntu
in type followign commands:
```
lspci
```
```
dmesg
```
```
cat /var/log/kern.log 
```

---

### Post by grantek on 2008-07-22
I'm having similar problems on the same motherboard. Firmware is F2, which is quite old.

I've upgraded the system from an older platform (PCI/AGP/DDR1/Skt 764 etc., MSI motherboard), and kept the existing x86_64 install on disk. I've also been messing around trying to install the latest ATI Catalyst drivers, so I hope nothing has been clobbered (I've uninstalled the driver and the problem still occurs, even when X isn't running)

I don't have the system in front of me, but the panic messages I've seen are related to disk I/O (from the filesystem level going down to the disk access level). It happens fairly predictably when I try to kick off an rsync backup of the system, or try to print the partition table using parted. In the BIOS, the SATA controller is in "Native IDE" mode. Other modes are "Legacy IDE", "SATA->AHCI" (don't know what this one is), and "RAID". I haven't tested them yet because they fail to boot properly (I think they just need an initrd rebuild).

In my testing, I tried the "dpkg" procedure from friendly-recovery in recovery mode - it panicked when I was booted into recovery mode, but I did the steps from the script manually while booted from a livecd and chrooted into the disk, and it worked fine. It installed a new version of linux-image-2.6.24-19-generic and the related dependencies, which I hoped would help, but it didn't.

I'll do some more testing (especially booted into a livecd), and see what I can find.

---

### Post by grantek on 2008-07-23
> **grantek said:**
> I've also been messing around trying to install the latest ATI Catalyst drivers, so I hope nothing has been clobbered (I've uninstalled the driver and the problem still occurs, even when X isn't running)
Argh - never mind me, it was something to do with the ATI proprietary driver. My system is stable in the livecd, the "-rt" kernel where I hadn't installed anything, and now the "-generic" kernel after a purge and reinstall.

If elwin_windleaf comes back with more information and anyone wants me to test anything with a stable system, PM me :)

Also, the "SATA->AHCI" mode I saw in the BIOS is basically "Native SATA" mode, in this mode the system has access to all the features SATA has that PATA IDE doesn't. I'm now running my system in this mode, it made no difference to my earlier problems, and seems to have no adverse affect on the working configurations :)

---

