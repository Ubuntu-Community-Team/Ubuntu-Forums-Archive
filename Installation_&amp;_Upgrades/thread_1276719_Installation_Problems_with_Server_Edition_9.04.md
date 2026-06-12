---
title: "Installation Problems with Server Edition 9.04"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by plaine on 2009-09-27
I've been having a wealth of problems trying to install Ubuntu Server Edition 9.04 on a completely new system, consisting of:

Gigabyte GA-EP45-UD3R (Rev 1.1)
4GB RAM
(4) 1TB Seagate Drives

All are brand new and I only plan on running Ubuntu on this server, and its never had (nor will it ever have) Windows or OS X or any other operating system for that matter.  

I followed all of the instructions, booting from a USB CD drive and going through the installation process.  I believe my problem may lie in the partitioning of the 4 drives, and if somebody could look over my configuration here and let me know where I'm slipping up, I'd like to end my 3 day fight with Ubuntu.  

I want to set these 4 drives up in a RAID 5 configuration.
I followed these directions, when it came time to do the partitioning:
[https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html)

However, when installation finished, it would not boot into Ubuntu, it just hung on me.  Upon searching some other documentation, it seemed like a key step was missing in that above list, and that was the "Bootable Flag" option.  So, after reading that that flag needed to be set to "yes" on another document, I re-installed and made the flag yes on the non-swap portion of those partitions on each drive.  So I'm thinking my partitioning/RAID must have some more problems, as the install completes each time.  Or maybe I didn't need a bootable flag, since this wasn't listed in that advanced installation guide link above.

On the "Partition Disks" screen during install, here's what I have:

RAID 5 device #0 - 3.0 TB Software RAID device
#1 3.0 TB ext3
RAID 5 device #1 - 24 GB Software RAID device
#1 24 GB swap swap

SCSI3 (0,0,0) (sda) - 1.0 TB ATA ST31000333AS
#1 primary 8.0 GB K raid
#2 primary 992.2 GB B K raid
SCSI3 (0,1,0) (sdb) - 1.0 TB ATA ST31000333AS
#1 primary 8.0 GB K raid
#2 primary 992.2 GB B K raid
SCSI3 (0,0,0) (sdc) - 1.0 TB ATA ST31000333AS
#1 primary 8.0 GB K raid
#2 primary 992.2 GB B K raid
SCSI3 (0,1,0) (sdd) - 1.0 TB ATA ST31000333AS
#1 primary 8.0 GB K raid
#2 primary 992.2 GB B K raid

I did have some confusion when setting up my RAID about which devices to select when it asks for how many devices, how many extra devices and then which sda1/sda2 directories.  I did 4 on the first, 0 on the second and then for the directories, I did those as listed above.  So maybe that's where my mistake is?

Is this correct if I want to setup RAID 5, making use of all 4 discs as part of the RAID?  My guess is not since its not working.  :)  Any help would be greatly appreciated.

---

### Post by stlsaint on 2009-09-27
should you choose to use raid...(ubuntu isnt very liking of raid at times) you may want to look into the [FakeRaid]("https://help.ubuntu.com/community/FakeRaidHowto") setup! if this isnt what your looking for  than explain exactly what your are having problems with(in more detail please) ie can you install period, or can you install but ubuntu isnt seeing all drives...those sort of things!!

---

### Post by plaine on 2009-09-27
Hmm.  I'm not sure what else you'd want details on, but yes, it's seeing all of the drives, as I've listed above, that's how I'm partitioning and details about that and RAID, however it just hangs when I finish installation and am re-booting.  It gives me an operating system error (no details as far as what the problem actually is however) and doesn't boot into Ubuntu at all.  I'm looking to see if the details I've posted above (taken from the partitioning screen) are correct.

---

### Post by stlsaint on 2009-09-27
hhmm...not to keen on raid in ubuntu because on my server i dont have raid setup. You may want to check out a [FakeRaid]("https://help.ubuntu.com/community/FakeRaidHowto") setup tho...if its not what you are looking for sorry...hopefully someone else will see this and come knocking for assistance.

---

