---
title: "Sata HDDs not recognized"
date: 2012-04-03
forum: Hardware
---

### Post by grammarxcore on 2012-04-03
My desktop is about seven years old with an older ASUS motherboard.  I have one Western Digital Caviar 160 GB IDE HDD, one Western Digital Caviar 250 GB SATA HDD, and two Seagate Barracuda 750 GB SATA HDDs installed that work perfectly with Windows XP. This weekend, I tried to install Ubuntu Server 10.04 and 11.10, Ubuntu Desktop 11.10, openSUSE 12.1, and Fedora 16 on the machine with limited success. My goal is install Ubuntu Server 10.04, but after it failed, I tried other distros to see if I could pinpoint the error.

All of the Live CDs were able to recognize the IDE harddrive and the WD 250 GB harddrive as well, but none were able to recognize the two Seagate drives. After spending several hours in Google, here are some things I've tried/pertinent information:
[LIST]
[*]Changing BIOS settings: I have looked through the BIOS settings multiple times, and the only setting I could find pertinent to other threads was "SATA Mode," which had "IDE" and "RAID" as options. I've tried both, but neither made Linux see the drives.
[*]Changing (some) boot settings: I've run the Ubuntu Server 10.04 install with "nodmraid", "all_generic_ide", and "pci=nomsi", which were settings that I could link to my problem with some legwork and/or frustration. I also installed without changing settings, and, with the current Ubuntu Server 10.04 disk, dmraid isn't automatically installed, so removing it after installation does nothing.
[*] "pci=nomsi" seems to do something with the two drives, because I get messages about "ata1/2/3", but it gives err=-11 and a time before the system retries the drive. After a few minutes of this, the system boots as it has, without recognizing the two Seagate drives.
[*]scsiadd: I'll admit that I have no idea what I'm doing, but this seemed promising after reading some threads. It doesn't find anything when I scan, although I might have the syntax wrong.
[*] sudo fdisk -l: This only gives me the 160 GB drive that Linux is installed on and the one SATA drive Linux can read, the 250 GB. The two Seagate drives do not appear.
[*] gparted and every other partition manager I've run do not recognize the two Seagate drives
[*] Both BIOS and the diagnostics it prints during boot recognize the two SATA drives. They disappear only after I do anything with Linux. I have used both successfully with Windows XP, one for several years, the other only for a couple of months, but both in this machine.
[/LIST]
Any help would be amazing. Like I said, I've spent quite a bit of time trying to figure it out, but I don't really know what's going wrong. If I can provide any logs or command output to help the process out, just let me know. I don't really know the proper things to include.

---

### Post by dandnsmith on 2012-04-04
1. have you tried putting either of the Seagate drives on the connector which works with the other SATA drive?

2. could you post the output of *lshw* (run as root), marked as a *code* item

---

### Post by oldfred on 2012-04-04
We have seen mixed SATA & PATA systems where BIOS promotes IDE drive to sda, but usually not other issues. As you suspected BIOS settings can make a difference.

Were SATA drives ever in RAID. That writes RAID meta-data that then gparted & Desktop installer fails as it does not work with RAID devices. If you are sure they are not RAID:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Some of the BIOS issues that others have posted:

> Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.



---

