---
title: "Mac Pro Cylinder (MacPro6,1 - Late 2013) and Thunderbolt 2"
date: 2014-03-13
forum: Hardware
---

### Post by bughuntr on 2014-03-13
I'm looking for some guidance.  I have a new Mac Pro cylinder (MacPro6,1 - Late 2013) aka the "trashcan Mac" on order for a project that I'm working on, and found out I need to run Linux on the system as well as the Mac OS.

Because of the project requirements I can't run the Linux install in a VM, and need the Mac to boot into Linux itself. The bigger problem is I need it to also see the 32TB Thunderbolt 2 drive array I have on order as well.

Has anyone had success installing and running ubuntu on the new Mac Pros (Mac6,1 - Late 2013) yet, and if so have you been able to use the graphics cards properly, and access external drives via Thunderbolt 2?

Any info would be helpful at this point.

Thanks!

---

### Post by zs3223 on 2014-05-16
I have documented how to install Ubuntu on the new Mac Pro cylinder here: [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)  My instructions only cover installing Ubuntu as the sole OS but you can modify my approach and keep OS X as well and dual boot.  All you need to do is shrink your OS X partition and create a separate partition for Linux before rebooting into the installer.  Then when you get to the part for creating the partitioning in Ubuntu make sure that you create your custom partitions in the appropriate location. Hope this helps.

> **bughuntr said:**
> I'm looking for some guidance.  I have a new Mac Pro cylinder (MacPro6,1 - Late 2013) aka the "trashcan Mac" on order for a project that I'm working on, and found out I need to run Linux on the system as well as the Mac OS.

Because of the project requirements I can't run the Linux install in a VM, and need the Mac to boot into Linux itself. The bigger problem is I need it to also see the 32TB Thunderbolt 2 drive array I have on order as well.

Has anyone had success installing and running ubuntu on the new Mac Pros (Mac6,1 - Late 2013) yet, and if so have you been able to use the graphics cards properly, and access external drives via Thunderbolt 2?

Any info would be helpful at this point.

Thanks!

---

### Post by 1clue on 2014-05-16
Do you still have Thunderbolt 2 monitor support?  How many monitors have you tried?

---

