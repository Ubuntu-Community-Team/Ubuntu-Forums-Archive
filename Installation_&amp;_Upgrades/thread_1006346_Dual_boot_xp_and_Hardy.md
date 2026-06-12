---
title: "Dual boot xp and Hardy"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by inadaze on 2008-12-09
Hey all,
I have seen a lot of problems on this forum related to installing Ubuntu on an XP hard drive.  But I found this tutorial and its seems far easier than I thought.
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Firstly, am I setting myself up for a hard time doing this?  Secondly, is it even possible with the hardware from a Dell Precision 390?

cheers,
Jay

---

### Post by Mark Phelps on 2008-12-09
According to what I read, your Dell workstation is configured to use Raid 0.  Haven't installed on a RAID machine, so I would suggest that you do two things: 
1) Try booting the liveCD first to ensure that Unbuntu is able to detect all your hardware and load the proper drivers.  Any driver problems you encounter while running the LiveCD may require a LOT of work to resolve after you install.
2) If you have no way to do a full image backup of your machine, wait until you get a reply from someone familiar with installing Ubuntu in a RAID environment.  If the install screws up your existing Windows partition, you may have a very hard time getting it back.

---

### Post by theozzlives on 2008-12-09
You could always do a WUBI install

---

### Post by linux_tech on 2008-12-09
RAID
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

install mdadm to be able to access your raid devices
The Linux Software Raid Howto: 
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Quick HOWTO: Linux Software Raid
[http://www.linuxhomenetworking.com/w..._Software_RAID](http://www.linuxhomenetworking.com/w..._Software_RAID)

Using mdadm to manage Linux Software Raid arrays
[http://www.linuxdevcenter.com/pub/a/...2/05/RAID.html](http://www.linuxdevcenter.com/pub/a/...2/05/RAID.html)

Ubuntu Fake Raid HOWTO In the community contributed documentation
[https://help.ubuntu.com/community/Fa...ght=%28raid%29](https://help.ubuntu.com/community/Fa...ght=%28raid%29)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Pumalite on 2008-12-09
And this:
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by inadaze on 2008-12-09
Thank you for your replies!

I get this feeling like Wubi is too good to be true.  Anyone have experience with this in comparison to dual booting?

It appears that wubi 8.10 supports RAID.

---

