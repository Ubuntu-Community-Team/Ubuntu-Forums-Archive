---
title: "No grub after install"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by punkrkr52 on 2009-05-01
I recently built a new gaming computer (spec below), and wanted to dual boot, using vista for gaming, and ubuntu as my main OS. After first installing vista, I booted into GParted and made ext2 and swap partitions (40gb and 2gb respectively), and rebooted into vista. Finally I installed Intrepid Ibex. After the installation (which completed without a hitch) I reboot, and my computer just boots straight into vista. I then ran the ubuntu live cd and checked my hdd partitions, and ubuntu is installed, but like I said, when I restart my comp theres no bootloader. Sorry If there's too much unnecessary information, I just don't like leaving out details. I did also have all my usb peripherals (mouse, card reader, mp3 player cable, and a gamepad) plugged in at install. I'm still not well versed enough in the ways of the linux that I would even know where to start. I googled extensively, but I must not be wording my query right because I can't find anything.

Computer Specicifations:
Motherboard: Asus M4A78-E 
CPU: AMD Phenom II 810 (2.6 ghz quad core)
Memory: G-Skill 2x2gb ddr2 1066
Video: Sapphire Radeon HD 4850
PSU: OCZ ModXstream 500w
HDD: Seagate Barracuda SATA 3.0gbs 750gig (OS's on here)
     Seagate IDE 140gig

---

### Post by BugFixBug on 2009-05-01
you might want to try to reinstall grub. though it should have been installed properly during ubuntu install

[here are the steps]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")


just a question:
why did you choose ext2 instead of ext3 ?

---

### Post by punkrkr52 on 2009-05-01
> **BugFixBug said:**
>  just a question:
why did you choose ext2 instead of ext3 ?

I wanted to start with Ibex so I could have something to roll back to in case I hose jaunty. I'm still relatively new with linux and I like to have a failsafe. BTW, I can upgrade ext2 to ext3 without formatting correct?

---

### Post by BugFixBug on 2009-05-01
> **punkrkr52 said:**
> I wanted to start with Ibex so I could have something to roll back to in case I hose jaunty. I'm still relatively new with linux and I like to have a failsafe. BTW, I can upgrade ext2 to ext3 without formatting correct?

hmm Intrepid Ibex had ext3 aswell, i recommend using ext3 next time.
you *can* convert ext2 to ext3. not sure how error prone it is:
[found this on google]("http://www.troubleshooters.com/linux/ext2toext3.htm")

---

### Post by punkrkr52 on 2009-05-01
> **BugFixBug said:**
> hmm Intrepid Ibex had ext3 aswell, i recommend using ext3 next time.
you *can* convert ext2 to ext3. not sure how error prone it is:
[found this on google]("http://www.troubleshooters.com/linux/ext2toext3.htm")

I thought ext3 was very new. I suppose I had incorrectly assumed since it was so new ibex wouldn't support it. I think I'll just wipe the partition and go with ext3. Thanks alot for your help. I'll give this all a shot and see what happens.

---

### Post by BugFixBug on 2009-05-01
ext4 is the newest version. ext3 is the current standard

---

