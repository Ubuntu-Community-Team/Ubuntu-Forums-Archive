---
title: "Ssd not showing up on OS"
date: 2019-01-28
forum: Hardware
---

### Post by spade93 on 2019-01-28
Hi,

Sorry if this has an answer on a different thread but my search didn't come up with anything that worked.

After a power outage my SSD wouldn't boot, on either windows (which i had it on) or ubuntu, the SSD shows up in the bios as correctly connected to my sata port, but doesn't show up in the boot option list, at least in UEFI, when i disabled the secure boot from the bios the ssd showed up in the bootlist, i guess it shows only on legacy mode ? but still won't boot from there (black screen).

Right now even windows bootable usb stick won't boot into installation menu, but when it did the installation didn't detect the SSD, i'm using an ubuntu mate live bootable usb and it's the same, during the install the ssd isn't detected nor it is in Gparted or Fdisk, dmesg command shows up the ssd though, and during the boot i get the following error : 

ata2.00: failed to set xfermode (err_mask=0x40)

i've read in a thread that i needed to initilize the drive from windows disk management (via a usb bootable stick) but since that one doesn't boot anymore is there any way to do it in ubuntu ?


Also the bios is abnormaly slow to load (3~4 min) until i can boot into anything, even the bios menu.

Here's what i tried so far and didn't work :

-Set W7 / W8.1 default settings in the bios
-Disabled secure boot to try and boot in legacy mode
-Set sata controller to RAID, AHCI, IDE

I'm quite desperate to make this work but i'm starting to wonder if the disk is dead at this point.

SSD model :  Samsung evo 860 msata 250gb
Linux (livecd) : Ubuntu mate 18.04

dmesg command output :
[https://ibb.co/Vp8HcQR](https://ibb.co/Vp8HcQR)
[https://ibb.co/DG9kRpw](https://ibb.co/DG9kRpw)

Thanks in advance for any help you can provide.

---

### Post by Autodave on 2019-01-28
Power outage (which can be with a power surge) and a BIOS that takes 3-4 minutes?  Sounds like there was a power surge that damaged something.  I see only one HD attached to SATA1.....is that correct?  If so, try disconnecting the HD (SSD) and see if that allows the BIOS to come up quickly like it should .  If the BIOS is now normal speed, then the SSD is probably bad.  If the BIOS still takes 3-4 minutes, then I would suspect a bad motherboard.

---

### Post by oldfred on 2019-01-28
Power failure or any abnormal shutdown often corrupts file system.
You may need chkdsk on all NTFS partitions and fsck on all ext4 partitions. You can run dosfsck or chkdsk on the FAT32 partition.

You cannot run chkdsk from Linux, but need a Windows repair disk or Windows installer with repair console.
The Linux ntfsfix, just turns on the chkdsk flag for NTFS to run chkdsk when booting. But if it does not boot that will not solve Windows issues.

       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sdb1
man dosfsck 

      
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by spade93 on 2019-01-28
> **Autodave said:**
> Power outage (which can be with a power surge) and a BIOS that takes 3-4 minutes?  Sounds like there was a power surge that damaged something.  I see only one HD attached to SATA1.....is that correct?  If so, try disconnecting the HD (SSD) and see if that allows the BIOS to come up quickly like it should .  If the BIOS is now normal speed, then the SSD is probably bad.  If the BIOS still takes 3-4 minutes, then I would suspect a bad motherboard.

Something worth noting, i forgot it in the op, when booting the ssd in legacy mode (Bios and not UEFI) it boots instantly, doesn't even let me access bios menu or BBS boot list, i have to unplug / replug cmos battery so i can access the bios, when the ssd is removed the bios is accessed instantly.


> [COLOR=#E8E7E3]You cannot run chkdsk from Linux, but need a Windows repair disk or Windows installer with repair console.[/COLOR]

Yea windows repair disk doesn't boot, it's stuck on the windows logo with the dotted circle, left it for an hour nothing happened, thing is before i started fiddling with things windows installer worked fine, i tried creating 2 usb sticks thinking the data was corrupted, one in bios legacy mode and one in uefi and both kept stuck in the windows logo.

Sudo parted -l only shows the usb stick i'm using for ubuntu mate, ssd doesn't show


To be honest, i'm novice in these kind of manipulaitons, so i didn't exactly understood everything you said, but the windows issues aren't gonna be solved just yet until i figure out why the installer usb stick won't boot
and to check the partitions in linux the ssd needs to be detected, which is not the case, the commands you suggested return either that there's nothing or that device doesn't exist.



Edit : the dosfsck command on the fat32 drive returned this :

> fsck.fat 4.1 (2017-01-24)
Logical sector size (1766 bytes) is not a multiple of the physical sector size.


Edit 2 : e2fsck commands returned this : 
> e2fsck 1.44.1 (24-Mar-2018)/dev/sda is in use.
e2fsck: Cannot continue, aborting.




---

### Post by oldfred on 2019-01-28
Is it seeing the flash drive as sda1, so it cannot run on mounted partition.

Does Disks and smart status show anything? Use icon in upper right corner of Disks.

If it boots too fast you may have fast boot on in UEFI, best to have that off when reconfiguring or making any changes. Only if system is not changed may you want it on.

---

### Post by Autodave on 2019-01-28
If you removed the battery, everything got reset to factory settings, so *fast boot*would have been turned back on.  You need to shut it off before proceeding with anything.

---

### Post by spade93 on 2019-01-28
[IMG]https://imgur.com/a/sLZka03[/IMG]>  [COLOR=#E8E7E3]Is it seeing the flash drive as sda1, so it cannot run on mounted partition.[/COLOR]

[COLOR=#E8E7E3]Does Disks and smart status show anything? Use icon in upper right corner of Disks.[/COLOR]
 

that's right, usb stick is showed as /sda[IMG]https://imgur.com/a/sLZka03[/IMG]


as for the fastboot, if you're referring to the option in windows i can't do that since it won't boot, and there's no option in the bios menu to disable it, but by resetting it, it allows me to access the bios so it's a non issue for now

---

### Post by oldfred on 2019-01-28
Please attach screen shots, do not post in line.
       If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

There is Windows fast start up & UEFI fast boot. Since Windows boots so slow Microsoft has both.
The fast boot in UEFI assumes no hardware or configuration changes, so UEFI does not scan system to write hardware configuration onto drive for operating system. It assumes everything is the same and immediately jumps to booting. 

Is drive seen by UEFI, not boot entry, but list of drives or devices.

---

### Post by spade93 on 2019-02-04
> **oldfred said:**
> Please attach screen shots, do not post in line.
       If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

There is Windows fast start up & UEFI fast boot. Since Windows boots so slow Microsoft has both.
The fast boot in UEFI assumes no hardware or configuration changes, so UEFI does not scan system to write hardware configuration onto drive for operating system. It assumes everything is the same and immediately jumps to booting. 

Is drive seen by UEFI, not boot entry, but list of drives or devices.

Sorry about the screenshot, attached screenshot kept loading to no end (bad internet) i'll use the advanced editor from now on.

I managed to boot into windows with external hard drive using windows to go, and nothing there either, ssd isn't detected in disk management or Diskpart, the only change that happened was after installing intel's rapid storage driver, a new menu showed up listing the ssd and its size in the bios.

Another info that i forgot and thought was irrelevant is before i set up this ssd i had a raid0 setup with 2 ssd that got fried up (i assume) since they wouldn't even show up in the bios.

Back to square one : 
-Ssd is detected in the bios both in sata configuration menu and intel rapid storage menu
-doesn't show up in linux (gparted / disks) nor windows (disk management / diskpart)

> There is Windows fast start up & UEFI fast boot

there's no option to enable or disable fastboot in the bios, and i disabled fast startup from windows)

Found another article saying that the drive won't show up unless Windows creates the system partition with the EFI Boot Sector but since i can't access the ssd from anywhere i don't know how to make that happen.

---

### Post by oldfred on 2019-02-04
Normally RAID 0 is not recommended.
It is used only for speed and was more back before SSD where hard drives were then slower.
If either drive is damaged, both drives then are lost as data is written in alternative tracks, not exactly how that is done with SSD as they do not have tracks but something equivalent.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

If a drive has RAID meta-data on it, then it will not be seen by standard Linux tools.
If now not part of RAID, you need to remove RAID meta-data.
[https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta](https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta)
       
 [http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)
sudo mdadm --detail-platform
[http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)
sudo mdadm --zero-superblock /dev/<nvmeXn1>
sudo mdadm --zero-superblock /dev/sda

---

