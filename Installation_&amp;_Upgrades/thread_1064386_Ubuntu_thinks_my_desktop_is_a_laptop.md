---
title: "Ubuntu thinks my desktop is a laptop"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by quantim on 2009-02-08
Hi all,

I've been running ubuntu on and off as my nix distro of choice for a few years now, and with the later versions i've run into problems when installing. Essentially ubuntu thinks my legacy desktop PCs are laptops.

When I install ubuntu, it does not detect my IDE drives and instead detects them as SCSI. Once the install is completed, instead of the desktop-style shutdown/restart icon (red circle with the line, like an off button), it displays the little green running man shutdown/restart icon, which is usually only for laptops. My desktop does NOT have a 'hibernate' option as it is not a laptop. This also means that when i 'shutdown' the computer it doesn't switch itself off, it gets to the point where the ubuntu black-bar has reached the end, then the computer just freezes. I imagine this is because ubuntu is looking for a laptop type of PSU rather than an ATX PSU

installing in 'expert' or OEM mode doesn't allow me to change this problem. I've searched these forums and had trouble finding anyone with a similar problem. 
i've been running ubuntu for months with this problem on this pc

SiS 730s MoBo
IDE 1 - 8GB (my /boot directory)
IDE 2 - 160GB (partitioned for a windoze install, along with my nix home directory)
here's an lspci output:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

and and fdisk -l output:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2614    20996923+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdb2            2615       19457   135291397+   f  W95 Ext'd (LBA)
/dev/sdb5            2615        8515    47393608+   7  HPFS/NTFS
/dev/sdb6           16175       19457    26370666   83  Linux
/dev/sdb7           16082       16174      746991   82  Linux swap / Solaris
/dev/sdb8            8516       16081    60773863+  83  Linux

this is silly, older ubuntu (and other linux distros) used to 'know' these were hda...

as a test, i installed Debian on an even older PC and it detected the drives fine, it knew they were hda not sda... but now i'm installing xubuntu and get the same problem as with ubuntu

aaargh i have NO IDEA why ubuntu is detecting it like this

any help i could get would be much appreciated :D

---

### Post by utnubuuser on 2009-02-08
Hi -- ...very strange.

There is something in synaptic called "laptop-detect", though I couln't tell you whether it's related or not.  It is something that's installed on a default install, (in HH anyway). Tried to call it up through a terminal, but the command is probably something other than the app-name.
Good Luck.

---

### Post by quantim on 2009-02-08
thanks for that, i realise this is 2 separate issues

1st: the later kernels are phasing out /dev/hdx style detection, something about UUID or whatever, so most all hdd's are detected as sdd's.
there's a fix for that here:
[http://ubuntuforums.org/showthread.php?t=415057&page=3](http://ubuntuforums.org/showthread.php?t=415057&page=3)
scroll down a bit, post by wallneradam

2nd: ubuntu thinks my desktop is a laptop. the fix above said to blacklist some programs in a /etc/modprobe.d/blacklist-local file to get around the kernel thinking hdd is sdd.

thanks for the info utnubuuser, i tried running "laptop-detect" after applying the above fix (just to see what would happen) and i got the following output:

quantim@quantimsbox:~$ laptop-detect
WARNING: /etc/modprobe.d/blacklist-local line 1: ignoring bad line starting with 'ata_piix'
FATAL: Error inserting battery (/lib/modules/2.6.24-21-generic/kernel/drivers/acpi/battery.ko): Operation not permitted

won't work cos i blacklisted ata_piix
i've added laptop-detect to my blacklist-local, i'm gonna try reboot now and see if it works as a desktop

if it works i'll have further questions, as i want to install ubuntu for some friends and want to stop this DURING the installation process.

---

### Post by quantim on 2009-02-09
okay, so i did the 'fix' i mentioned in my last post, and killed my boot process, it only boots into initramfs, with which i can't undo any of the changes that i've done. i think i killed grub by removing the UUIDs and replacing them with the relevant /dev/hdX values... i've kind of given up as that dual-boot drive is messy anyhow.

BUT i have just done a fresh install of Xubuntu and gotten the same problem

HOW, WHY DOES UBUNTU THINK THESE DESKTOPS ARE LAPTOPS?

during the installation process, regardless of the hardware configuration, ubuntu thinks their are SATA not PATA drives - separate issue, apparently

i have to install the latest iso of ubuntu (both normal and 'alternate' discs) on various combinations of 4 different motherboards, 3 different PSUs, 4-5 different PATA hard drives and a variety of PCI cards. Regardless of the configuration, ubuntu installs a bunch of laptop-specific software, such as CHECKING MY BATTERY LIFE... what battery? it's a desktop!

i'm just surprised googling and searching these forums hasn't shown anyone else with the same problem - i've been getting it for about a year!

is there anyway to blacklist specific modules during installation?
e.g. disabling 'laptop-detect' and other laptop-speciric modules?

---

### Post by quantim on 2009-02-09
for the record, i could not solve this problem

i've changed to TinyMe linux and it picked up the drives & all other hardware with no problems

---

### Post by spcwingo on 2009-02-09
Did you try acpi=force in you kernel line of your grub menu.lst?  The reason I ask is I had the same shutdown problems on legacy boards (pre-Y2K).  A quick edit of the menu.lst cleared that right up!  ;)

---

