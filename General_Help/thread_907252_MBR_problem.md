---
title: "MBR problem?"
date: 2008-09-01
forum: General Help
---

### Post by Pandora's Box on 2008-09-01
I'm getting this error when moving on to the 2nd phase of the Wubi Ubuntu installation(after it tells you to reboot).

It kicks me to the GRUB prompt instead of continuing normally, by pressing INSERT I was able to obtain this information:

Booting GRLDR hard drives: 1, int13: F00064A3, int15: F000F859

get_diskinfo(80), int13/41(80), version=AA300005, int13/48(80), err = 0, C/H/S = 16

383/16/63, sector count/size = 312500000 / 0, int13/08(80), version = 0, C/H/S = 1023 /

55/63, int13/02(80), err=0,

**Warning: MBR cylinders (19453) is not equal to the BIOS one (16383).**

**Warning: MBR total sectors (312512445) is greater than the BIOS one (312500000).**

Some buggy BIOSes could hang when you access sectors exceeding the BIOS limit.

LBA, C/H/S = 19453/255/63, sector count/size = 312512415/512

After doing a search for on one of these warnings, I was lead to a topic recommending me to download 'fstest' and run it with certain flags to create a log.

Here is the output:

info C:\
version: 1.0 build 3
part_base: 0x3F (0M)
part_leng: 0x116786C1 (142576M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x5CD2CE8

inode C:\$MFT
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

inode C:\.
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

list C:\
000070AA             0  [dell]
00003FDF             0  [NVIDIA]
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

list C:\ubuntu\install\boot
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

inode C:\ubuntu\install\boot\vmlinuz
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

comp C:\ubuntu\install\boot\vmlinuz
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18

Just as a note, in the past, I once had Wubi Ubuntu installed on this same exact PC but had to un-install it due to space constraints. Right now I have a new IT related job where I need to become more proficient in Linux, so would be greatly appreciative if anyone could assist me.

Thank you,

-PB

---

### Post by Pandora's Box on 2008-09-02
Bump

---

### Post by caljohnsmith on 2008-09-02
Some older BIOSes do not recognize files/partitions that lie beyond the first 137 GB of your HDD. Is it possible that the C:\GRLDR file or maybe menu.lst is outside of that limit on your HDD? That might be the problem.

---

### Post by Pandora's Box on 2008-09-02
Hmm, around 50 gigs free on my 160 gig drive. But maybe the file may have been fragmented and moved deeper into drive past 137 when my drive was more fragmented.

I've defragged and it didn't seem to fix it, though. PC is using Dell bios, I have an XPS-400 but made a few customizations to it myself.

---

### Post by caljohnsmith on 2008-09-02
Do you have a "menu.lst" in the C:\ root directory? That's where Grub4DOS normally puts it I think. I think that getting dropped into the grub prompt is exactly what can happen if the menu.lst is simply missing. Also, on start up, do you get an option to select between Windows and Grub4DOS? Or does it immediately throw you into the Grub prompt?

---

### Post by Pandora's Box on 2008-09-02
> **caljohnsmith said:**
> Do you have a "menu.lst" in the C:\ root directory? That's where Grub4DOS normally puts it I think. I think that getting dropped into the grub prompt is exactly what can happen if the menu.lst is simply missing. Also, on start up, do you get an option to select between Windows and Grub4DOS? Or does it immediately throw you into the Grub prompt?

Not in c:\ root, but in C:\ubuntu\winboot, and C:\ubuntu\install\boot\grub.

After loading BIOS, I have the NT boot-loader with the option of loading WinXP pro, or 'Ubuntu'.

---

### Post by caljohnsmith on 2008-09-02
What is the contents of the C:\ubuntu\install\boot\grub\menu.lst file?

---

### Post by Pandora's Box on 2008-09-03
#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso automatic-ubiquity noprompt debug debug-ubiquity xforcevesa boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   acpi=off noapic nolapic
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Read-Only Demo (Live CD Desktop)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-amd64.iso quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by bean123 on 2008-09-03
Actually, this is caused by a limitation of grub ntfs driver, please defrag your drive and see if it works.

---

### Post by Pandora's Box on 2008-09-03
Freed up space, defragged, re-installed. Same error. 61.8GB free of 139GB.

---

### Post by bean123 on 2008-09-04
Please try the new fstest.exe at [http://grub4dos.sourceforge.net/grub4dos/](http://grub4dos.sourceforge.net/grub4dos/)

---

### Post by llh11456 on 2008-09-06
If games like [buy wow gold](http://www.usfine.com/world-of-warcraft-usa-c-51.html) Quake and Doom defined action gaming in the gaming world, Need for Speed was the definition of racing games. Need For Speed, [maple story power leveling](http://www.usfine.com/Maple-Story-PowerLeveling-c-98.html) or NFS for short has been around since almost the beginning of when computer gaming gained importance. [runescape power leveling](http://www.usfine.com/runescape-powerleveling-c-90.html)Need For Speed is [runescape powerleveling](http://www.usfine.com/runescape-powerleveling-c-90.html) a racing game in which the player chooses cars and then races on various tracks.welcome to our website[wow gold](http://www.usfine.com/)

---

