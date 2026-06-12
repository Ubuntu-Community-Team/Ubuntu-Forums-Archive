---
title: "How to install over existing dual boot?"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by bigkahuna on 2005-12-07
Hi,

I searched the wiki and forums and haven't found an answer, so here goes:

I've got two systems, both are dual boot Kanotix / XP with Grub.  The Kanotix partition has about 5 gb plus another 500 mb swap space.  I'm still a bit of a Linux newbie, so how do I safely install Ubuntu Breezy and replace the Kanotix install without messing up the existing XP partition?  Does Ubuntu use Grub as a boot manager?

Thanks!

---

### Post by matthew on 2005-12-07
When you boot the Ubuntu install disk you will have the opportunity to make any changes to your disk partitions that you want to make, including leaving them alone as you would want to do with the XP partition. Just tell the Ubuntu disk partitioner during setup to format the current Kanotix partition and then install Ubuntu there.

Once installed Ubuntu will configure grub and will make sure the XP installation is included.

It's easier than it sounds...here's a wiki page that goes into more detail:
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by aysiu on 2005-12-07
1. Know exactly where each partition lives.
2. Choose "manually edit partition table" instead of "erase entire hard drive" during installation.
3. Install Grub to the MBR.

---

