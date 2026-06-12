---
title: "System hangs: Requires physical reboot with reset button."
date: 2014-02-21
forum: Hardware
---

### Post by cliff-peeples on 2014-02-21
I'm having a world of a time trying to troubleshoot the my MP system...

Specs:
4x Intel Xeon E7430 processors
16 GB ECC Registered DDR2
SuperMicro X7QCE mainboard in a 2U rackmount server chassis
ATi Radeon 6450 (the onboard video is ATi ES1000 and was flaky at best so I've disabled it in BIOS)
3x 3TB in RAID5
3x 2TB in RAID5

1x Samsung SSD 128GB

Only 4 of the 6 SATA channels onboard are functional, so I'm using those four for the 3TB drives and one of the 2TB drives.  I had to purchase a PCI Sata Controller card to control the other two 2TB drives and the Samsung SSD.

First, I installed 12.04LTS.  About 10~15 minutes into operation, the system locks up tight with Unity.  Manual reset required.  Did this again two times in a row, so I figured I'll try to install 13.10.  Same issues.  Went back to 12.04 and changed the environment to LXDE, and it didn't seem to mind (it didn't hang roughly every 20 minutes of being in operation).  I wasn't fond of LXDE though, not really my cup-o-tea.  Every time I think to go pull the syslog to check for errors, it will lock up.  I get sidetracked easily I suppose. :(

I even tried to run Memtest from the linux boot, and memtest doesn't seem to load up at all and run any tests.

I'd appreciate some pointers before I try another distro.  I want to make sure I'm not having a hardware problem since I just took delivery of this system early this week.  

Thanks for any advice, or if you can point me in the right direction.  I want to believe it's something as simple as a video driver incompatibility for whatever reason, and not that it's the system mainboard.

---

### Post by cliff-peeples on 2014-02-21
Just an update.  Going back to basics and pulled all but 4 sticks of ram and I'm now running memtest86.  If all goes well with 4GB I'll increase to 8GB and rerun the test.

---

### Post by cliff-peeples on 2014-03-04
Final update.  I'm currently running with 12 of the 16GB of RAM the system shipped with.  One or more of the 4 ram modules is defective, so I'm shipping them off to be replaced.  

Very surprised that I couldn't even boot into memtest86, never had a problem with it before even with multiple defective modules.

---

