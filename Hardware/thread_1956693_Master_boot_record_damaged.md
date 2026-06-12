---
title: "Master boot record damaged"
date: 2012-04-11
forum: Hardware
---

### Post by JBU55 on 2012-04-11
Dear Ubuntu users,

I am experiencing problems booting my laptop on which windows xp is installed. I removed the harddisk from the laptop and connected it as an USB hard drive to another windows xp laptop. There I see the harddisk is healthy but empty and cannot be explored for files. When I connect the harddisk to a laptop that runs Ubuntu the hard disk is accessible and readable and I can recover all my files from it. 
My question: in order to prevent a reinstallation of the many user programs on the laptop, is there a way to fix the master boot record of the windows xp damaged installation from within ubuntu. I do not have a possibility to boot from CD or from USB on the original laptop.

Thank you in advance,

Jane

---

### Post by oldfred on 2012-04-11
This would use a Windows install/repairCD. You can use a Windows 7 repairCD also to install a boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From a Ubuntu liveCD you can install lilo's boot loader which works like Windows in the MBR in that is just jumps to the PBR - partition boot sector to continue booting. New versions of Ubuntu may also need to install synaptic to enable universe repository, if lilo not found which means it is not enabled as default.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

I think this can directly fix the MBR for Windows. It uses syslinux and can either be installed into Ubuntu liveCD or USB or downloaded as a full bootable liveCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by JBU55 on 2012-04-11
Thank you for the advice. The problem is solved now and the system boots.

Greetz,

Jane

---

