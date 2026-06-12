---
title: "quad boot Linux mint grub"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by konnorrigby on 2009-08-09
Ok, sooooo... i have two hdd's in my computer and have three os's that look like this

```

/dev/sda1
Windows XP

dev/sda2
empty space/ unallocated

dev/sdb1
linux mint gloria    (boot)

dev/sdb2
Kubuntu

dev/sdb5
swap

dev/sdb7
swap


```

so my question is can i install a new distro with keeping the grub that is on linux mint? i like that one kuz you can chang the background easer.


--thanks in advance

---

### Post by presence1960 on 2009-08-09
yes you can do that, but you need to install GRUB of the new distro to it's partition rather than MBR. Then I would recommend chainloading all distros off the Mint GRUB (menu.lst). As long as all your distros (except Mint) have their respective GRUB on their own partition you can do this. The added benefit is when each distro upgrades their kernels you won't have to edit your Mint GRUB (the one that boots) to use the new kernels. 
Here is my fdisk output:

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   5  Extended
/dev/sda2            5223       19843   117443182+  83  Linux
/dev/sda3           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux
raz@raz-desktop:~$ 

```
sda5 is Jaunty my boot GRUB and is on MBR of sda.
sda7 is Mint 5
sdb2 is Sabayon 4.1
These are my linux OSs. sda2 & sdb1 are ext 3 data partitions. sda3 is NTFS data, sda4 is Windows 7.

here is jaunty's menu.lst after jaunty entries:

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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Linux Mint x64 (on /dev/sda7)
root		(hd0,6)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Sabayon Linux x86-64 (on /dev/sdb2)
root		(hd1,1)
chainloader     +1

```

---

### Post by tgalati4 on 2009-08-09
Yes, but realize that different distros come with different versions of GRUB so that you can expect breakage.  

Usually I just install a new distro then load the live CD of Mint and run from a terminal:

sudo grub-install /dev/sda2 (or where your main distro is located)

Then I have to cut and paste the entries for the new distro.  It's tedious, but I can't think of a better way to do it.

Normally you can install GRUB to each distro's partition and then have a master GRUB menu.lst that simply points to each GRUB using the configfile command.

That gives you a two-step boot, first grub comes up with a list of distros, then you click on one and it brings up the grub for that distro.  Kind of a pain, but it's a way to keep each version of grub separate.

---

### Post by presence1960 on 2009-08-09
> **tgalati4 said:**
> Yes, but realize that different distros come with different versions of GRUB so that you can expect breakage.  

Usually I just install a new distro then load the live CD of Mint and run from a terminal:

sudo grub-install /dev/sda2 (or where your main distro is located)

Then I have to cut and paste the entries for the new distro.  It's tedious, but I can't think of a better way to do it.

Normally you can install GRUB to each distro's partition and then have a master GRUB menu.lst that simply points to each GRUB using the configfile command.

That gives you a two-step boot, first grub comes up with a list of distros, then you click on one and it brings up the grub for that distro.  Kind of a pain, but it's a way to keep each version of grub separate.
All 3 of my distros have different GRUB versions. When you chainload them it is just like when you chainload windows. When you select a chainloaded item from your boot GRUB menu it points to the GRUB installed on the first sector of the partition of that particular distro and then that GRUB takes over. No breakage. You also do not have to edit your boot GRUB to boot upgraded kernels in the other distros since their respective menu,lsts are auto updated with the new kernel info. I'd prefer to do that with the 2 step boot because it takes all of 2 seconds and no copy & pasting to my boot GRUB menu.lst which with all those distros and kernel upgrades is very tedious indeed!

Ubuntu has GRUB 0.97, Mint has it's special version of GRUB and sabayon 4.1 has GRUB 2. No problems ever with the chainload method.

---

### Post by markbuntu on 2009-08-10
+1 for chainloading. The chainloader does not care what is at the other end it just hands off the boot to whatever is there and gets out of the way. The problem with grub is that grub1 will not boot to a grub2 stage 1.5

Chainloading is really the only foolproof method for booting multi distros. No cutting and pasting and no problems with kernel updates or anything else. I often replace distros and even then do not need to change the mbr grub if I use an old partition it points to. When I do edit the menu.lst it is to change the name to remind me what I have there which I sometimes do eventually.


title		Chainload Ubuntu 8.04 amd64
root		(hd1)
chainloader	+1

#This entry added for Debian5 (Lenny) amd64 on sdc

title		Chainload Debian
root            (hd2,0)
chainloader     +1

#This entry added for Mandriva 2009.1KDE
title		Chainload Mandriva
root		(hd2,6)
chainloader	+1

#This entry added for SUSE11.1 on sdd1

title		Chainload SUSE11.1
root		(hd3,0)
chainloader	+1

#This entry added for Jaunty on sdd3
title		Chainload Ubuntu Jaunty 9.04 kernel 2.6.29
root		(hd3,2)
chainloader      +1

---

