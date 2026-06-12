---
title: "Tri Boot Sharing /home"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by coldfusion1313 on 2009-08-24
I am going to install Open Solaris and Fedora 11 on my laptop along with Ubuntu 9.04 already installed is there all way that I can have all three OS share the same /home directory?

---

### Post by Tclarkie on 2009-08-24
i dont think so, you need separate partitions

---

### Post by Tclarkie on 2009-08-24
and its set up differently, so it wouldn't work

---

### Post by coldfusion1313 on 2009-08-24
Can i also see all these OS in grub?

---

### Post by stlsaint on 2009-08-24
no dont share all OS with /home but you will be able to see all in Grub menu lst! thats how you will select them...i recommend you install what ever distro of ubuntu that you will use the most last as i know jaunty will just add the rest of the kernels out of the other OS automatically with no issues...fedora is a big bully and will take everything onto its self and you will have to edit menu.lst manually to get the others onboard.

---

### Post by presence1960 on 2009-08-24
> **coldfusion1313 said:**
> Can i also see all these OS in grub?

Whichever GRUB is on the MBR of the hard disk that boots will work. you will have to install GRUB to the partitions of the other distros and chainload them off GRUB on the MBR. I will show you my fdisk output as well as the menu.lst of Jaunty. jaunty's GRUB is on MBR of my first hard disk to boot so that takes over when I start my rig. here is fdisk output:

```
raz-sabayon raz # fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14621   117443151    5  Extended
/dev/sda2   *       14622       19696    40764937+   7  HPFS/NTFS
/dev/sda3           19697       25064    43118460    7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d562f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48301   387977751   83  Linux
/dev/sdb3           48302       60801   100406250    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       17107   137411946   83  Linux
/dev/sdc2           17108       19457    18876375   83  Linux
raz-sabayon raz # 
```
sda1 is extended containg logicals: sda5 is Ubuntu Jaunty (GRUB is on MBR), sda7 is Linux Mint GRUB is installed on sda7 not MBR)
sda2 Is Vista (just installed that for some testing)
sda3 is windows data partition
sda4 is Windows 7 RC
sdc2 is Sabayon 4.1 (GRUB is installed on sdc2 not MBR)
With this setup when I boot Jaunty's GRUB takes over since it is on MBR.

I will give you the last section of menu.lst for Jaunty as jaunty's GRUB is on MBR of hard disk that boots first. Note chainloading of Mint 5 and Sabayon:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows 7 RC (loader)
rootnoverify	(hd0,3)
savedefault
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Linux Mint x64 (on /dev/sda7)
rootnoverify    (hd0,6)
chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title		Sabayon 4.1
rootnoverify	(hd2,1)
chainloader	+1
```

The advantage of chainloading is no editing menu.lst when each distro has a kernel update. When kernels are updated only the menu.lst of that particular distro is updated. So for instance when I boot and I choose Sabayon or Mint 5 it hands off to their menu.lsts which brings up their GRUB menu which will have all updated kernels in it. 

The alternative is not an appealing one to me because to boot all the other distros off the GRUB in MBR you will have to manually edit the GRUB on MBR to create entries for the new kernel. The chainload method is easier & neater. You van also keep entries that are chainloaded if you install another distro there by just changing the title in it's chainload entry. For instance if I removed Sabayon 4.1 and installed Kubuntu to that same partition, all I would need to do is change the title from Sabayon 4.1 to Kubuntu and it would be ready to boot.

---

