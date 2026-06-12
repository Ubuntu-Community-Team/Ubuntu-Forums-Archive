---
title: "HP Workstation RAID shows up as two separate drives"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by dracule on 2009-09-11
Hello, I am working on an HP Workstation Wx9300

It has 2 500gb SATA drives Configured by the Nvidia Bios manager to be in split raid setup, that is i combined them both into 1 TB drive. In Vista, when I went to install, it showed just the one drive and I was happy, it installed and everything worked as one drive. 

In linux, it is a different story, when i went to install it showed two separate drives. 

So I am wondering, is there anyway i can even dualboot? And also the more important question: how the heck do I install this on this array?

---

### Post by ronparent on 2009-09-11
The two separate drives will show if you use the stadard live cd for installation. Assuming that you have a MB raid chipset follow the directions at this site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You were wise to ask before proceeding - others who didn't found out the hard way how to destroy a raid set (data not hardware)! The installation should leave you with dual boot.

---

