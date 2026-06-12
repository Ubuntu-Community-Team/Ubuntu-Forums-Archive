---
title: "secondary Hard Disk not recognized"
date: 2011-11-03
forum: Hardware
---

### Post by d3uterius on 2011-11-03
Hi everybody, i have a desktop with 2 hdds, on one win7 and on the other one a ntfs data partition and a smaller partition where i have installed ubuntu 11.10. During the installation, it asked me where to save the boot loader, it only let me choose the ntfs data partition on the second disk. The Grub menu doesn't appear when i start the pc, and also win7 can't see that ntfs partition anymore...If you have any idea how to delete the boot loader from that harddisk, so i be able to use it again? I can't format it, i have important data on it..
Thanks..:)

---

### Post by JRV on 2011-11-03
Can you change the boot order in the BIOS?
I think this would be a lot easier, and safer.
Then do a ```
sudo apt-get update-grub
``` to regain access to your Windows.

---

### Post by oldfred on 2011-11-03
You never ever install grub2's (or grub legacy's) boot loader to the PBR of a NTFS partition. I do not even know why they even allow it. You should have had the choice of the MBR of your second drive. All NTFS partitions have to have a NTFS signature (not grub) and if bootable additional Widows info in the PBR.

Post this to see detail:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

NTFS partitions keep a backup of the PBR - partition boot sector. Testdisk from the Ubuntu liveCD can restore the backup.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.

---

