---
title: "Prepare partions screen empty"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by shadycuz on 2009-03-29
I have been looking for a solution for 2 days so I decided I would just post. I tried to install ubuntu 7.04 and the live cd wouldn't boot, I got some weird job control tty message and was left at a command prompt. So I tried a brand new HDD, but that didn't work either. So I tried the latest version of ubuntu and I chose install at the main menu and when it get's to prepare partitions the screen is just blank. It doesn't list any thing. When I'm on ubuntu live cd fdisk -l wont return any thing not even error, but on other live cd's it says can not read hard drive. Qtparted says error partitions cant be out side of disk. When I When I boot windows and use partition magic, I can see all partitions on the drive. I think it might be a hardware problem? System board is gigabyte GA-MA69GM-S2H, HDD is raptor 160gig.

---

### Post by cariboo on 2009-03-29
Is the drive detected in the BIOS? You may need to change a setting in your BIOS in order for the drive to show up. Check and see if there is an ACHI setting in your BIOS, if there is use that. Unless you have a fully up to date Windows install you may not be able to boot into Windows, so make sure you are up to date before making the change.

Jim

---

### Post by shadycuz on 2009-04-02
AHCI Did not work either. How ever their was a third settings that really made booting up the live cd and installing fast, and that was IDE legacy.

---

