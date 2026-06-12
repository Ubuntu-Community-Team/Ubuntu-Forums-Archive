---
title: "problem installing ubuntu in dual boot on raid 0"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by y_garti on 2009-05-19
hello everyone
i have a computer that is on raid 0 and with vista
i want to install ubuntu on that computer so i can chose which operation system to run 
ubuntu for everything
vista for gaming (direct x 10) and a little work from home
when i insert my ubuntu 9.04 CD (the original CD) my ubuntu installation doesn't know that my computer is using a raid 0 striped disks and let me chose one of my 2 HD to install (it also doesn't know that i have vista install on it) 
i really want to install ubuntu on that computer i am sick of vista
thank you

---

### Post by dstew on 2009-05-19
If you try to do a regular Ubuntu install it will probably destroy the RAID. The only easy way to do it would be to use the Vista partition management tools to shrink the Vista file system, and create a regular un-
RAIDed file system out of the freed up space on which to install Ubuntu.

Do you know if the Vista RAID is a software or semi-hardware RAID (also called "FakeRaid")?

If it is a software RAID, you might be able to install Ubuntu onto it using the Alternate Install CD. However, you will not be able to dual-boot because the grub boot loader is not able to mount striped RAID filesystems. You would have to create a small RAID 1 or create a separate un-RAIDed partition to mount to the /boot mountpoint. Maybe the Windows booter can boot a Linux kernel from a RAID, but I don't know.

If it is FakeRaid, you might be able to install to it. See the [Fake Raid How-To]("https://help.ubuntu.com/community/FakeRaidHowto"). I do not know of anyone who has successfully installed Ubuntu to  a Vista RAID and had Vista survive. If you can do it kudos and be sure to let everyone know how you did it.

Probably your best option is to install using [Wubi]("http://wubi-installer.org/"). This installs Ubuntu as a Windows file onto the Windows file system. Then your RAID will stay intact.

---

### Post by y_garti on 2009-05-19
ok i already free a 40 GB of free space using partion manager and my raid is hardware (my mother boared do the raid)
i looked at the fakeraid howto and even try to do it myself but when i do 
sudo dmraid -ay 
i get
ERROR: isw device for volume "Volume0" broken on /dev/sdb in RAID set "isw_bhajhcifda_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_bhajhcifda_Volume0" [1/2] on /dev/sdb
RAID set "isw_bhajhcifda_Volume0" was not activated
so if there is any way i can install it without brakeing vista to a million pices i'll be glad

---

### Post by y_garti on 2009-05-20
i also try wubi and in the end of the installation i didn't get to the gnome it enter me to a terminal (i never used wubi but i think that i suppose to log in gnome and not to a terminal)
also in the terminal lots of the commands doesn't work (like su sudo and much more)
if someone know how to help me installing in any way ubuntu on my computer I'll be glad
thanks

---

### Post by Tomatosoup on 2009-05-20
I had the same problem.
Use the Alternate Install CD, it will probably see your RAID setting. With me it did.

But then GRUB doesn't want to install...
So you can't boot into Ubuntu.

---

### Post by Tomatosoup on 2009-05-20
> **dstew said:**
> If you try to do a regular Ubuntu install it will probably destroy the RAID. The only easy way to do it would be to use the Vista partition management tools to shrink the Vista file system, and create a regular un-
RAIDed file system out of the freed up space on which to install Ubuntu.

How could one create an un-RAIDed file system without destroying existing data?
I myself have a software RAID (configured via BIOS).
A RAID-0 setting.

---

### Post by Tomatosoup on 2009-05-20
Well, I found this:
[http://support.euro.dell.com/support/edocs/systems/xlob/dtg/en/drives.htm#wp1208823](http://support.euro.dell.com/support/edocs/systems/xlob/dtg/en/drives.htm#wp1208823)

But I don't see anything I can use that will not destroy my existing data.

---

### Post by y_garti on 2009-05-20
so let me see if i understand what you are saying 

i have a raid 0 with vista and Ubuntu don't know how to work with that configuration ?

---

### Post by dstew on 2009-05-20
> How could one create an un-RAIDed file system without destroying existing data?
You need to shrink the current RAID filesystem and partitions, then create new partitions out of the unallocated space. Shrinking the RAID may cause data loss if done improperly. You would need to use Vista tools to do that, if it can be done at all.

@y_garti:

Try **dmraid -r** to list all the potential RAIDs. Perhaps the error message is from a messed-up RAID, or some old metadata that is present but not part of a potentially active RAID. And yes, the Ubuntu install process may not see your RAID, especially if it is a FakeRAID. You would need to use dmraid to do that.

---

