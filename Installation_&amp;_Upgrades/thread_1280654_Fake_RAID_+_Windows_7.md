---
title: "Fake RAID + Windows 7"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by DEmberton on 2009-10-02
Hi,
 
I've been rebuilding my Dell desktop system with two new 1TB drives, which I've setup as RAID1 using the onboard "hardware RAID" system (Intel something or other). I've installed Windows 7 x64, which worked fine and saw the two disks as one.
 
Now I'm trying to install Kubuntu 9.04. When I first tired, I noticed the install was seeing two seperate disks which obviously wasn't correct. Lots of reading about "fake RAID" later, and I discovered I need the "alternate" CD. Sure enough, installing with alternate CD it recognizes the RAID setup and appears to get through the install.
 
After installing, reboot and it boots straight into Windows with no Grub menu.:( I went back and rebooted off the live CD, and that shows the ext3 partitions on the two drives with what looks like the correct content, so that part of the install worked and obviously respected the RAID setup.
 
I went back to the alternate CD, and paid a bit more attention this time and set the partition to bootable, but after going through the install again this time my PC won't boot at all. "No boot device".
 
Tried again, switched off the bootable flag, still "no boot device".
 
Went back to Windows CD, and ran the boot repair and now I have it booting to Windows again. At least Microsoft are on the ball.:P
 
So how do I sort this out?
 
The drive is 1TB. Windows installs a 100MB partition at the start of the disk, and I've created a 150GB partition to install Windows on. Inside Windows I created another 700GB partition for data, and my intent was to use the remaining ~150GB for a Linux install.
 
The three I created are all marked as primary, but the Kubuntu install wouldn't let me do anything other than create logical partitions for Linux. Do they need to be primary?
 
Thanks for any help.

---

### Post by afrauen on 2009-11-05
You might want to read the following thread, I think a number of people (including myself) are stuck with similar issues:

[http://ubuntuforums.org/archive/index.php/t-1305082.html](http://ubuntuforums.org/archive/index.php/t-1305082.html)

---

### Post by Mark Phelps on 2009-11-05
Did your Dell system come with Win7 preinstalled?  Or did you install it yourself? If so, was that to an existing NTFS partition, or was that to an unformatted drive?

Asking because Win7, by default, when installed to clean drives (and when preloaded by some OEMs), installs a recovery partition that also acts as a boot partition, in addition to the standard NTFS partition.  This recovery/boot partition appears to pose major problems with GRUB2 booting.

---

