---
title: "Samsung Series 7 Chronos Ubuntu Install"
date: 2012-03-04
forum: Hardware
---

### Post by kmas on 2012-03-04
This thread was originally started to fix a Samsung Series 7 Chronos boot install. But there's a bunch of other issues I encountered therefore I'm turning this into a general thread for the device issues on Ubuntu. 

**Boot Issues: **
_How to boot from USB on a Samsung Series 7 Chronos: _
First go into BIOS and enable legacy devices boot. Save changes, reboot, press esc at startup screen, then you should see your USB. If this doesn't work, Make sure you not plugging the USB into the USB 3.0 Port (blue port). If you want that port to work anyways boot into windows, and install [the drivers for USB 3.0]("http://www.samsung.com/us/support/owners/product/NP700Z3A-S06US")

_How to Boot into Ubuntu on a Samsung Series 7 chronos: _
If you already booted into windows and enabled the option to allow you to fast boot into Windows, you just enabled UEFI, and created a gpt partition for booting into machine. Try the troubleshooting steps from here: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2) , you will most likely have issues and error messages similar to [this post]("http://ubuntuforums.org/showpost.php?p=11740543&postcount=8") and [this is why]("http://ubuntuforums.org/showpost.php?p=11741206&postcount=9"). You can either [disable UEFI from BIOS, [use FixParts]("http://ubuntuforums.org/showpost.php?p=11748978&postcount=11") to remove GPT partition all together] or you can [use[ Boot Repair CD]("http://ubuntuforums.org/showpost.php?p=11771380&postcount=12")] or if you feeling like RAMBO [Here is the full [UEFI Ubuntu Booting tutorial]("https://help.ubuntu.com/community/UEFIBooting"), This might be helpful skill to know in long run, when we move to Windows 8+ machines]

**Drivers Issues**
_Mouse and Touchpad_
*11.10:*
If you installed 11.10, your mouse is probably detected as a PS2 Generic Mouse. Synclient will show that your drivers are not loaded. Didn't find a fix for it, but [here is the thread]("http://ubuntuforums.org/showthread.php?p=11777563"). [The workaround is to install kernel 3.2 and configure your conf.d/]("http://ubuntuforums.org/showpost.php?p=11772195&postcount=13") 
*12.04:*
If you upgraded from 11.10, you might encounter same issues as 11.10. On a clean install however, your mouse multitouch will work. Here is [how to properly configure synclient]("http://ubuntuforums.org/showthread.php?t=1401645") and [here are few tips]("http://tombuntu.com/index.php/2011/10/31/fix-for-touchpad-trouble-in-ubuntu-11-10/") and [this helped ]("http://askubuntu.com/questions/69010/is-there-a-way-to-tell-where-synclient-gets-its-information-from")a lot, [Here ]("http://manpages.ubuntu.com/manpages/oneiric/en/man4/synaptics.4.html")you can find what all the synclient options mean. []("http://forums.opensuse.org/english/get-technical-help-here/hardware/387890-synclient-not-reflecting-xorg-conf-settings.html")

_Graphics Card_
*Switchable Graphics*
Our laptop has switchable graphics that aren't quite optimized yet, [Read more about it here]("https://help.ubuntu.com/community/HybridGraphics").  [These guys report]("http://linux-hybrid-graphics.blogspot.com/") 3.3 kernel has full hybird graphics functionality. [Here is a thread]("http://ubuntuforums.org/showthread.php?t=1930450") that gives more information. 
*Drivers*
Both 11.10 and 12.04 default drivers work just fine, if you install the ati drivers provided by ubuntu's "additional drivers" program, you probably will end up with no Compiz/GPU. The drivers from the ati website don't work. X will fail to start. just turn off the switchable graphics options previously mentioned with default drivers and you should be fine. In 12.04 you can use Catalyst drivers [here's how]("http://ubuntuforums.org/showpost.php?p=11777783&postcount=17"). 


**Power Consumption/FAN and Noises**
This I got from [this post ]("http://superuser.com/a/384679") credits to [zackrspv]("http://superuser.com/users/112155/zackrspv") and [mas]("http://superuser.com/users/116294/mas")
_Power: _
*I tried passing parameters on boot-up (e.g. pcie_aspm=force), but did not help. Utilized powertop, plus juniper as well but could never get power below 28W consumption. Without the tweaks I get around 33W. Getting battery life around 2.5 hours whereas I'm getting 5.5 to 6 hours in Windows 7.*
There's a work around on 12.04 that can get you 5 hrs of battery life by using Ati drivers [http://ubuntuforums.org/showpost.php?p=11777783&postcount=17](http://ubuntuforums.org/showpost.php?p=11777783&postcount=17), suggested by [miatawnt2b]("http://ubuntuforums.org/member.php?u=263498").

---

### Post by miegiel on 2012-03-04
The machine has a SSD and a regular harddisk? If so, wich does the BIOS use to boot?

---

### Post by kmas on 2012-03-04
Oki it looks like it uses the 1TB HDD not the 8GB SSD. at boot when you press escape it doesn't even show any of the SSD. the only bootable hard drive is Samsung-hn-mb101MBB. from a quick google search looks like the 1 TB HDD

---

### Post by kmas on 2012-03-04
I tried to follow the steps to restore GRUB2 on the USB BOOTABLE DRIVE

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda --force
grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
ubuntu@ubuntu:~$ 
```

after reboot it failed like expected GRUB restore didn't work,I then tried another step to force install grub into every partition on my hard drive. There are 2 partitions approx 100MB generated by windows, not sure which one holds the MBR. The force install returns no errors, but after reboot, I get right into windows.

```

ubuntu@ubuntu:~$ sudo umount /dev/sda
umount: /dev/sda: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy
ubuntu@ubuntu:~$ ls /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0d7d62f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8012 MB, 8012390400 bytes
256 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(266305, 4, 4)

Disk /dev/sdc: 32.0 GB, 31991533568 bytes
64 heads, 32 sectors/track, 30509 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000027f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30509    31241200    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1 --force 

```

---

### Post by miegiel on 2012-03-04
To start GRUB the ubuntu installation changes the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record"). At one of the last questions during the installation, you are asked if the location the installer found is correct. (something../sda or so)

You could fix it this way (if that's not to daunting).
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by miegiel on 2012-03-04
> **kmas said:**
> I tried to follow the steps to restore GRUB2 on the USB BOOTABLE DRIVE

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda --force
grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
ubuntu@ubuntu:~$ 
```

after reboot it failed like expected GRUB restore didn't work,I then tried another step to force install grub into every partition on my hard drive. There are 2 partitions approx 100MB generated by windows, not sure which one holds the MBR. The force install returns no errors, but after reboot, I get right into windows.

```

ubuntu@ubuntu:~$ sudo umount /dev/sda
umount: /dev/sda: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy
ubuntu@ubuntu:~$ ls /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0d7d62f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8012 MB, 8012390400 bytes
256 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(266305, 4, 4)

Disk /dev/sdc: 32.0 GB, 31991533568 bytes
64 heads, 32 sectors/track, 30509 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000027f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30509    31241200    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1 --force 

```

Never install GRUB  to a partition. Always put it on the disk!

So use */dev/sda* and not */dev/sda**[COLOR="Red"]1[/COLOR]***

here:
```
sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda
```

*/dev/sda /dev/sdb* are disks and */dev/sda1 /dev/sda2* are partitions on /dev/sda

You're mixing the 2 up when you mount too. It should be:
```
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
```

---

### Post by kmas on 2012-03-04
I was trying the partition because any attempts to write to the disk won't work. It gave me an error just like the error for the partition. After reading more around I think the root of my problem might be the UEFI enabled on my BIOS. disabling it, and installing Ubuntu will still not let me boot into it, it gives me a black screen. 

looks like thse might be the solution. but looks like work i cant complete tonight.

[http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I might be wrong, if you think my assumption is wrong chime in please.

---

### Post by kmas on 2012-03-05
I stepped back and tried what you suggested over again. Here are the results. 

```
root@ubuntu:/home/ubuntu# sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda
grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/home/ubuntu# sudo grub-setup -d /media/982ce4d5-c8fe-439e-ab77-afc89b20e91a/boot/grub /dev/sda --force
grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..


```

Here is the second method. 

```

root@ubuntu:/home/ubuntu# sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0d7d62f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 8012 MB, 8012390400 bytes
256 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(266305, 4, 4)

Disk /dev/sdc: 32.0 GB, 31991533568 bytes
64 heads, 32 sectors/track, 30509 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000027f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30509    31241200    c  W95 FAT32 (LBA)
root@ubuntu:/home/ubuntu# sudo mount /dev/sda1 /mnt
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt /dev/sda --force
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.


```

Both Proven to be unsuccessful.

---

### Post by oldfred on 2012-03-05
Grub used to directly install to a gpt drive, but used blocklists which it does not like. Maybe they have changed it to force the use of a bios_grub partition. I have installed all the newer versions of Ubuntu thru 12.04 to a gpt drive but created the bios_grub 1MB partition first and then had no issues.

Or are you booting in UEFI mode. Is first partition efi? fdisk does not work on gpt use gdisk or parted.

You have to download gdisk from synaptic or apt-get install.
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. 
BIOS Boot Partition of 1 MiB for partition alignment.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

You can set bios_grub flag in gparted or with command line with gdisk or parted: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

BIOS Boot Partitio only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)

If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be the first partition. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

---

### Post by kmas on 2012-03-08
Oki, sorry for late reply. I recieved a replacement unit, because other unit was defective. First thing I notice is that the fdisk gives me a different result. 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0d7d62f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   316876799   158334976    7  HPFS/NTFS/exFAT
/dev/sda3       316876800  1906708479   794915840    f  W95 Ext'd (LBA)
/dev/sda4      1906708480  1953523711    23407616   27  Hidden NTFS WinRE
/dev/sda5       316878848  1906708479   794914816    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8012 MB, 8012390400 bytes
246 heads, 40 sectors/track, 1590 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15646719     7822336   73  Unknown

Disk /dev/sdc: 32.0 GB, 31991533568 bytes
255 heads, 63 sectors/track, 3889 cylinders, total 62483464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01a0db78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    62483463    31241700+   c  W95 FAT32 (LBA)

```

Second thing that I noticed is that in the BIOS there is a place where you can enable uefi. It is disabled right now and the legacy boot option is seleceted. 

the discovery of the sda partition looks like this. 
```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA SAMSUNG HN-M101M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system  Flags
 1      2048s        206847s      204800s      primary   ntfs         boot
 2      206848s      316876799s   316669952s   primary   ntfs
 3      316876800s   1906708479s  1589831680s  extended               lba
 5      316878848s   1906708479s  1589829632s  logical   ntfs
 4      1906708480s  1953523711s  46815232s    primary   ntfs         diag

```

here is my sfdisk
```
ubuntu@ubuntu:~$ sudo sfdisk -l -uS

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS/exFAT
/dev/sda2        206848 316876799  316669952   7  HPFS/NTFS/exFAT
/dev/sda3     316876800 1906708479 1589831680   f  W95 Ext'd (LBA)
/dev/sda4     1906708480 1953523711   46815232  27  Hidden NTFS WinRE
/dev/sda5     316878848 1906708479 1589829632   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 974 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/246/40 (instead of 974/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048  15646719   15644672  73  Unknown
        start: (c,h,s) expected (0,51,9) found (0,32,33)
        end: (c,h,s) expected (1023,245,40) found (973,245,40)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdc: 30509 cylinders, 64 heads, 32 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 30509/64/32).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *        63  62483463   62483401   c  W95 FAT32 (LBA)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty


```

and here i the gdisk
```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ABE50E2B-E0C9-42AF-A404-1C3D3E50B562
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5485 sectors (2.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Microsoft basic data
   2          206848       316876799   151.0 GiB   0700  Microsoft basic data
   4      1906708480      1953523711   22.3 GiB    2700  Windows RE
   5       316878848      1906708479   758.1 GiB   0700  Microsoft basic data



```

reports no sign of gpt. that might be due to the fact that on the first unit i received i enabled this option that helps windows boot faster, and i think it is through it that my partition was altered. will attempt the install again and report back.

---

### Post by oldfred on 2012-03-08
If a drive is gpt and you install Windows in MBR mode it erases the gpt partitions but only partitally. Windows does not see the backup partition table that it saves, but Linux tools do see the backup can get confused. Your gdisk output shows the issue.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by taxi333 on 2012-03-16
I have the same laptop and I was having problems booting up Ubuntu after the installation 
but I was able to fix this using an Ubuntu CD and using the application Boot-Repair  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

This application is very easy to use  if you have questions let me know.

PS: I love my Samsung Chronos :D

---

### Post by miatawnt2b on 2012-03-17
Just got mine last night and immediately wiped and installed oneiric and a 3.2.0rc4 kernel.

to get the touchpad working properly, edit the file 
/usr/share/X11/xorg.conf.d/50-synaptics.conf
and add the following lines

	Option "FingerLow" "1"
	Option "FingerHigh" "1"
	Option "FastTaps" "1"
	Option "SingleTapTimeout" "360"

also I've disabled the radeon kernel module until hybrid video is better supported.

Also used this link to get the wireless working again after the 3.2 kernel.

[http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/](http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/)

and some more tweaks
[http://forum.notebookreview.com/samsung/640919-request-samsung-700z-linux-guide.html](http://forum.notebookreview.com/samsung/640919-request-samsung-700z-linux-guide.html)

That's about all the farther I've gotten.  I still have very high power usage on battery at 29W. I need to get that down a bit more.

At this point I am at a loss to go much further, I'm guessing the hardware is just too new to be well supported in Ubuntu. 

If anyone has more ideas please post them here. We need a thread for the series 7... there really isn't much info out there about it.

-J

---

### Post by kmas on 2012-03-19
> **taxi333 said:**
> I have the same laptop and I was having problems booting up Ubuntu after the installation 
but I was able to fix this using an Ubuntu CD and using the application Boot-Repair  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")



This application is very easy to use  if you have questions let me know.

PS: I love my Samsung Chronos :D

This also worked for me. What I did is, I enabled UEFI, and tried installing again. After encountering the same issues I just used your link. 

> **miatawnt2b said:**
> Just got mine last night and immediately wiped and installed oneiric and a 3.2.0rc4 kernel.

to get the touchpad working properly, edit the file 
/usr/share/X11/xorg.conf.d/50-synaptics.conf
and add the following lines

	Option "FingerLow" "1"
	Option "FingerHigh" "1"
	Option "FastTaps" "1"
	Option "SingleTapTimeout" "360"

also I've disabled the radeon kernel module until hybrid video is better supported.

Also used this link to get the wireless working again after the 3.2 kernel.

[http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/](http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/)

and some more tweaks
[http://forum.notebookreview.com/samsung/640919-request-samsung-700z-linux-guide.html](http://forum.notebookreview.com/samsung/640919-request-samsung-700z-linux-guide.html)

That's about all the farther I've gotten.  I still have very high power usage on battery at 29W. I need to get that down a bit more.

At this point I am at a loss to go much further, I'm guessing the hardware is just too new to be well supported in Ubuntu. 

If anyone has more ideas please post them here. We need a thread for the series 7... there really isn't much info out there about it.

-J

Hey J,

I might turn this thread into how to Samsung Series 7 issues and link up my findings to the main Post, will appreciate your feedback. try the synclient command what do you get, are you able to see the Touchpad option under mouse and touchpad settings. look at this thread: [http://ubuntuforums.org/showthread.php?p=11777563](http://ubuntuforums.org/showthread.php?p=11777563)

---

### Post by miatawnt2b on 2012-03-19
Hey J,

I might turn this thread into how to Samsung Series 7 issues and link up my findings to the main Post, will appreciate your feedback. try the synclient command what do you get, are you able to see the Touchpad option under mouse and touchpad settings. look at this thread: [http://ubuntuforums.org/showthread.php?p=11777563](http://ubuntuforums.org/showthread.php?p=11777563)[/QUOTE]

I actually tried to start one as I thought people might get confused from the first couple posts...

[http://ubuntuforums.org/showthread.php?t=1942839](http://ubuntuforums.org/showthread.php?t=1942839)


here is a list of my synclient config settings.  It's working pretty well. I am now running 12.04 with the 3.2.0-19-generic kernel and pretty much the touchpad just works properly.
```
root@Chronos:# synclient -l
Parameter settings:
    LeftEdge                = 130
    RightEdge               = 3130
    TopEdge                 = 123
    BottomEdge              = 2159
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 175
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 79
    HorizScrollDelta        = 79
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0502639
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 318
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 19
    VertHysteresis          = 19
    ClickPad                = 0

```

---

### Post by kmas on 2012-03-19
we had same idea. :) look at my first post. I linked your posts in some of the fixes I suggest. Added a bunch of other issues as well.

---

### Post by miatawnt2b on 2012-03-19
> **kmas said:**
> we had same idea. :) look at my first post. I linked your posts in some of the fixes I suggest. Added a bunch of other issues as well.

Perfect, lets use this thread.

So... as I said I installed 12.04 and let it update last night. after the updates, keyboard backlight, wifi, touchpad work out of the box.

I then installed gnome-common gnome-session and gnome-session-fallback just because I hate Unity.

then comes the hybrid graphics...

First install synaptic and purge all instances of radeon/ati/fglrx. This will also require the removal of the xserver-xorg-video-all metapackage but that's not a big deal.  I did not uninstall the jockey package

then I downloaded the Catalyst 12.2 driver from ATI/AMD and installed. upon install I rebooted (didn't need to run aticonfig)

I'm now running the ATI driver, and my power is between 15.4W and 20W depending on use.  Battery life is about 5 hours.

one last problem at this point... Catalyst administrative tools allow you to set the video card to Intel. I selected this, it prompted for reboot. I rebooted, and X refuses to start.  I was never able to recover from this, probably due to my linux lack of knowledge. I tried removing xorg.conf, loading intel and vesa driver instead, reinstalling catalyst tools from command line.  I couldn't get X to start properly, so I ended up reinstalling the whole system from scratch.  I won't be clicking that option again until we can figure out exactly what's going on.

Anyhow, for the most part, I'm happy.
-J

---

### Post by miatawnt2b on 2012-03-19
ok, found a ppa from the hybrid graphics thread
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

ppa:sarvatt/intel-sna

Installed the xserver-xorg-video-intel - 2:2.18.0+git20120317.e31d9dac-0ubuntu0sarvatt2~sna 

I'm afraid to try and set the graphics to Intel though... :)

---

### Post by lublin on 2012-04-07
> **miatawnt2b said:**
> 
one last problem at this point... Catalyst administrative tools allow you to set the video card to Intel. I selected this, it prompted for reboot. I rebooted, and X refuses to start.  I was never able to recover from this, probably due to my linux lack of knowledge. I tried removing xorg.conf, loading intel and vesa driver instead, reinstalling catalyst tools from command line.  I couldn't get X to start properly, so I ended up reinstalling the whole system from scratch.  I won't be clicking that option again until we can figure out exactly what's going on.


Hi. I just got myself a new laptop and has been looking around a loot for the best solution and yours seems to be on track. I tried the use intel video card option and as you said there was some problems, but I managed to solve it.

amdconfig has the following flags for handling it

  --px-dgpu
       Activate discrete GPU (High-Performance mode), must re-start X to take effect
  --px-igpu
       Activate integrated GPU (Power-Saving mode), must re-start X to take effect

So to revert to functional discrete gpu use `sudo amdconfig --px-dgpu` and restart lightdm. I also managed to start X properly with the integrated gpu. I got the dialog about no working configuration found and i chose tried some options which didn't work but after another restart of lightdm i got to login.

glxinfo gives me a "BadRequest" so the intel driver isn't working as it should, probably because it tries to use glx from catalyst. So no GL but it seems my power usage dropped from ~23W to ~18W although I wouldn't count on these numbers too much.

---

### Post by miatawnt2b on 2012-05-02
There is a fix for the direct rendering problem on the integrated GPU. first post step2.

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

Things sure have come a long way in the two months I've had my Chronos. Graphics works really well now.
-J



> **lublin said:**
> Hi. I just got myself a new laptop and has been looking around a loot for the best solution and yours seems to be on track. I tried the use intel video card option and as you said there was some problems, but I managed to solve it.

amdconfig has the following flags for handling it

  --px-dgpu
       Activate discrete GPU (High-Performance mode), must re-start X to take effect
  --px-igpu
       Activate integrated GPU (Power-Saving mode), must re-start X to take effect

So to revert to functional discrete gpu use `sudo amdconfig --px-dgpu` and restart lightdm. I also managed to start X properly with the integrated gpu. I got the dialog about no working configuration found and i chose tried some options which didn't work but after another restart of lightdm i got to login.

glxinfo gives me a "BadRequest" so the intel driver isn't working as it should, probably because it tries to use glx from catalyst. So no GL but it seems my power usage dropped from ~23W to ~18W although I wouldn't count on these numbers too much.

---

### Post by Sda1986 on 2012-05-06
I have problem to come back from UEFI boot. I have a Samsung Chronos 7 700z3a-s1

I boot\installed one time with UEFI and now i cannot come back, and install without UEFI...

Do you have the same problem?

Soon I'll post my advance with this laptop.

My posts: [http://ubuntuforums.org/showthread.php?t=1969571](http://ubuntuforums.org/showthread.php?t=1969571)

---

### Post by Martin James on 2012-11-07
Bringing this back to USBs if I may, I've just - finally - got my new Samsung 7 Chronos to boot off a USB.

There are significant posts around on checking accessibility using <ESC> to get the BIOS Boot Menu: I don't get <ESC> as an option - and spent hours trying to find out how to switch it on. I only get F2 (SETUP) & F4 (RECOVERY). And re-ordering to put (all 3) USB options up the list in the SETUP BOOT Priority Order did nothing. 

But under BIOS 'Advanced' there is a 'Fast BIOS Mode' which was defaulting to [Enable]. Looking at the description of this field it says "'Disabled' means ... legacy USB is supported." Sure enough, once switched to 'Disabled', off it went! Slower, perhaps, but then I was having trouble getting F2 pressed quickly enough anyway. 

Now I can get on with GParting the hard drive.

[PS:  This is my 1st ever post, on any forum, anywhere, about anything.  All down hill from here then.]

---

### Post by caliber556 on 2012-12-01
**Guide to install 12.10 on the 17" Chronos (NP700Z7C-S01UB).** 

It is using Nvidia, not ATI. Everything (important) works out of the box except for the infamous ACPI/kworker kernel issue that is behind the excessive power consumption and fan noise. Much more than the dual graphics. Like stated in teh first post of this thread, the alleged fixes (pci=noacpi, etc.) do not work. In fact they make it worse: 100% Core 1 utilization instead of "typical" 75%. The "good news" (sorta) is that the problem is intermittent and goes away after a number of restarts and jerking the power cord in and out. It is not a Samsung-only issue, as it affects many notebooks - primarily newer ones with I7.

Posted it in another thread though think it belongs here:
[http://ubuntuforums.org/showpost.php?p=12382951&postcount=5](http://ubuntuforums.org/showpost.php?p=12382951&postcount=5)

---

