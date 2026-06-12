---
title: "HDDs not detected"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by paul8472 on 2009-10-28
I'm not sure if this is a bug or my own incompetence but:

I have the following system:


 500GB - WesternDigital WD500AKS-0 - empty/unpartitioned
160GB - Maxtor 6YM160M0 - Contains various paritions including Ubuntu 9.04
160GB - Maxtor 6YM160M0 - empty/unpartitioned
 

All of the above HDD are connected to a built in SATA controller (ICH8R) on my Intel motherboard.


 I currently have no problems with my Ubuntu installation.


 I just tried to run 9.10 RC and after the GUI loaded it told the 2 Maxtor drives contained errors etc. It couldn't detect anything on either 160GB and said there were numerous bad sectors.


 At this point I ran the full installer to see what the partition tool in the installer had to say. It could detect the 500GB WD but described the 2x160GB Maxtors as being a 320GB RAID array. No wonder it thinks the drives are corrupted! These drives are not in a RAID array.  They were in a RAID away previously (in an old Win installation).



 Any ideas why the partitioner thinks they are?  Is there some old flag set on the drives that 9.04 was ignoring but 9.10 picks up?



 I've posted it as a bug on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470") but I think it's probably being ignored as it may not really be a bug.

---

### Post by dabl on 2009-10-28
There seem to be a rash of hard drive detection and "quality" issues, with 9.10:

[http://ubuntuforums.org/showthread.php?t=1301697](http://ubuntuforums.org/showthread.php?t=1301697)

Yesterday I read a thread where a guy was in the process of replacing an allegedly defective hard drive when a bug report was found on the topic. You might twiddle the BIOS SATA "mode" setting between AHCI and "legacy IDE" or whatever you have, and see if that makes a difference in the detection of it.  I've had at least one motherboard/BIOS where the SATA mode needed to be set to "legacy" for initial installation, but then it would boot and fine with it set back to "AHCI" after installation was finished.

---

### Post by paul8472 on 2009-10-30
I spent some time last night playing around with the AHCI/IDE/RAID settings to no avail.  In the end I decided to install 9.04 on a new partition and then upgrade.  I left it upgrading this morning so hopefully it will be done when I get home!

This isn't a very satisfactory solution though as I understand that you need to do a clean install to get all the benefits of ext4.  Also, I'll have to manually install GRUB2.0 (which is bound to end in tears).

---

### Post by paul8472 on 2009-10-30
No luck on the upgrade.  I'm getting more convinced this a bug now so i've posted further dtails [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470")

---

