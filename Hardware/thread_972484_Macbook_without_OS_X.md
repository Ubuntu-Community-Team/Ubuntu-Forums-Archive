---
title: "Macbook without OS X"
date: 2008-11-05
forum: Hardware
---

### Post by Choobie on 2008-11-05
So my friend is a dumb dumb and wiped his Mac hard drive with the intention of installing Ubuntu 8.10. He tried to follow the guide at first but got frustrated because he had an outdated version of Boot Camp, and had other problems or whatever, but that is irrelevant now.

So he threw in the live CD and went through the install procedure, opting to reformat the entire drive because he wasn't given the option of resizing partitions (Apple lock down?).

After install he reboots, and finds that his computer won't boot. He gets a white screen with a folder that has question marks, or some other cute BS like that basically telling him something is wrong (but not giving any kind of real diagnostics information).

So he doesn't have is Mac CDs anymore to try and restore, nor does he want to fork out the money for a new copy of Mac OS X. Not to mention he really wants to run Linux. Do you guys have any idea on what we can do?

Thanks!

---

### Post by claudius753 on 2008-11-05
YOu don't need to have os x.  Just boot the live cd, and when you install, make sure you delete all of the partitions and use the entire drive for ubuntu (partitioning however you like).  That should wipe out the GPT and instead make the drive a normal MBR disk.

Once done, when you power on the system, you should get the folder screen and it will then hand off control to GRUB.

You can also take a look at rEFIt if you do happen to want to get OS X back on the system and dual boot linux.  [http://refit.sourceforge.net/myths/]("http://refit.sourceforge.net/myths/")

---

