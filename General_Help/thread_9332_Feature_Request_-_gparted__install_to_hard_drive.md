---
title: "Feature Request - gparted / install to hard drive"
date: 2004-12-27
forum: General Help
---

### Post by apwiggins on 2004-12-27
I've been demonstrating Ubuntu LiveCD to friends and family over the last few weeks.  Several are interested in trying further.  They like the fact that they can test Ubuntu to see that all hardware works (printer, sound, NTFS partitions, etc).

One of the gaps is the ability to resize NTFS partitions to prepare for an Ubuntu install using a partition re-sizing tools such as gparted.

Use Case / Vision:
Phil demonstrates Ubuntu to his brother Jerrold.  Jerrold has a store-bought computer which came pre-configured with one NTFS partition containing Windows XP.  Jerrold has a single 40Gb hard drive which is about 50% full.

After seeing the potential of Ubuntu, Jerrold consents to having a small part of his disk allocated to an installation of Ubuntu.  

Scenario #1:
Using the Ubuntu LiveCD, Phil and Jerrold use the Ubuntu gparted tool to resize the existing 40Gb hard drive partition containing the single NTFS partition.  After resizing the existing partition to 30Gb, the remaining 10Gb is unallocated and available for a new Ubuntu installation.

Following a reboot, Ubuntu provides a boot menu option: Install Ubuntu to hard disk using unallocated space.

Scenario #2:
Using the Ubuntu LiveCD, Phil and Jerrold use the boot menu option: Install Ubuntu to hard disk (resize current partitions).

Ubuntu boots and provides as part of the installation sequence QtParted (on top of QtEmbedded) (is there an equivalent gtkEmbedded??) which permits the existing 40Gb partition to be resized to 30Gb.  The net effect is a single 30Gb NTFS partition.  The remaining 10Gb is unallocated and available for a new Ubuntu installation.  As part of the follow-on sequence, Ubuntu provides options to install itself within the remaining 10 Gb of unallocated free space.

---

### Post by enHuxley on 2005-02-20
bUmP!

 - This is a great idea, and if Im not aware that it is added currently to the list of things to do, I second the idea for GParted's addition future releases of Ubuntu

---

### Post by misGnomer on 2005-02-21
I believe that the Ubuntu developers are planning/hoping to eventually create a single live+installation CD which can be used for booting into live sessions, system maintenance and also regular installs. Even if the unified live+install CD might be some way in the future, the planned improved installer should integrate partitioning tools (GParted?) into the post-Hoary release (v5.10). The actual plans and timetables may differ, but if some feature makes sense, it will be added to Ubuntu sooner or later.  :-)

Meanwhile the somewhat more experienced among us can use e.g. the live [SystemRescueCD](http://www.sysresccd.org/) (~100MB) for managing partitions etc. as we help new users to get Ubuntu installed.

---

### Post by readingboy on 2005-03-12
[QUOTE=misGnomer]I believe that the Ubuntu developers are planning/hoping to eventually create a single live+installation CD which can be used for booting into live sessions, system maintenance and also regular installs. Even if the unified live+install CD might be some way in the future, the planned improved installer should integrate partitioning tools (GParted?) into the post-Hoary release (v5.10). The actual plans and timetables may differ, but if some feature makes sense, it will be added to Ubuntu sooner or later.  :-)

Meanwhile the somewhat more experienced among us can use e.g. the live [SystemRescueCD](http://www.sysresccd.org/) (~100MB) for managing partitions etc. as we help new users to get Ubuntu installed.[/QUOTE]

 Hi All,

I'm not sure why we need to wait for the live+install CD for GParted to be included on the live cd. It's a package that should be easy to add and it would have obvious benefits. It's part of the installation workflow for many users who have gone beyond the Live CD trial period, have decided to use Ubuntu, and wish to include it on their harddrive alongside their current OS. Not having this available is a roadblock to Ubuntu installations. Many people don't know about the SystemRescueCD (I just discovered it myself as a Linux user for the last 5 years) and potential users will assume they need to purchase something like PartitionMagic for repartitioning Even if we are successful in educating these potential Ubuntu users about SystemRescueCD, the hurdle of downloading a 100 MB iso,  burning it to CD, and then using QTParted (which isn't as nice as GParted) seems like an obstacle that is quite easily removed. Why are we not making the entire installation process as easy as possible? We're really only talking about one additional software item installed. Is there an issue with this I'm not aware of? 

Please reconsider holding GParted back from the Live CD.

-- Craig

---

