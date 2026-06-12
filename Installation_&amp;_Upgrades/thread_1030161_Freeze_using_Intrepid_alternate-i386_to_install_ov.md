---
title: "Freeze using Intrepid alternate-i386 to install over Feisty on Acer Aspire 1315LM"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by BuggyBY on 2009-01-04
Hello,

I tried to use the alternate-i386 disc for Intrepid to install over my previous installation of Feisty, which ran fine apart from a refusal to update any packages giving the following error message:
```
E: Internal Error, Could not perform immediate configuration (2) on libc6
```
I had searched for a fix to this problem and performed [the steps suggested]("http://ubuntuforums.org/showthread.php?t=653177") to no avail, so I opted for a more radical method and used the alternate installation disc for 8.10 to completely overwrite my system with a fresh installation as suggested in [UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes").
Having backed up all my data, I reformatted my sole ext3 partition (about 27GB in size) and used it as my root directory. 
File system creation, DHCP and other hardware recognition proceeded without any snags, until it came to the "Select and install software" step, which has been stuck on 29% proclaiming that it is "Preparing openoffice.org-core" for well over an hour now.

Any suggestions would be appreciated.

---

### Post by Pumalite on 2009-01-04
Make sure you have a cd without errors. Start with doing md5sum on the iso, burn at 4x or less, do not use CD-RW, check CD integrity before install.
Post your specs.

---

### Post by BuggyBY on 2009-01-04
The CD was checked for integrity both before and after installation attempt, and passed as valid both times, so that should in theory not be the problem.

My laptop is the standard unmodified Acer Aspire 1315LM model (German version, mind you) - AMD Athlon XP 2500+ at 1.86GHz, 60GB hdd, Pioneer DVD-RW drive, 512 MB DDR RAM, internal floppy drive (quite rare for its time), 15" TFT screen supporting 1024x786 resolution, S3 ProSavage8 graphics controller ... most other hardware specs are available on its [Amazon UK webpage]("http://www.amazon.co.uk/dp/B0000AXM4T"), bless their greedy little hearts. The batteries (replaced in 2005-06) are sadly rather run down at the moment, lasting maybe 25-30 minutes on a good day, but apart from that it has no hardware problems I'm aware of.

It had been running Feisty quite successfully and without any problems, apart from the aforementioned little apt issue regarding libc6. The single partition reserved for Ubuntu (designated hda7 by Feisty and sda7 by the installer's partition utility) is a logical one, but GRUB never seemed to complain about it.

Unfortunately the abortive installation attempt seems to have screwed up the hard drive's boot sector, so I currently cannot get into the former dual-boot's Windows OS (though the [Super GRUB disk]("http://www.supergrubdisk.org/") should fix that, once I've burned another one).

---

### Post by BuggyBY on 2009-01-04
Minor update: Using Super Grub Disk, I have now put Windows XP Professional (German) as the only bootable option in the MBR. Might come in handy for diagnostics or further details regarding hardware, I dunno.

---

### Post by Pumalite on 2009-01-04
Did you do md5sum on the iso?

---

### Post by BuggyBY on 2009-01-04
Alas, I didn't when I had the chance, and now it's gone with the rest of the old Feisty system. There didn't seem to have been any problems with the download, though, and I have never had checksum errors from downloaded files on this connection as far as I can remember. While I suppose there's a first time for everything, shouldn't the CD's integrity check have caught any irregularity?

---

### Post by Pumalite on 2009-01-04
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
I'd clean the burner's lens too.

---

