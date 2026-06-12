---
title: "How To Upgrade ???[Problem With Live CD or somthin]"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by satyanash on 2009-03-13
i have ubuntu 7.10 on my PC. i have the CD for the 8.10 version and want to upgrade to 8.10. but when i put the CD in and click on add CD-ROM in the software sources third party tab it shows a mounting bar and then gives an error saying something like this :

ERROR SCANNING THE CD
"E:Could not open file /cdrom/dists/intrepid/main/binary-i386/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor), W:Hash mismatch for: main/binary-i386/Packages, E:Could not open file /cdrom/dists/intrepid/restricted/binary-i386/Packages - open (2 No such file or directory), E:Unable to determine the file size - fstat (9 Bad file descriptor), W:Hash mismatch for: restricted/binary-i386/Packages"

How do i upgrade please tell and also about this problem and i dual boot my system with windows XP and linux ubuntu 7.10.

also i have all my personal data on another partition so need to worry about that.

---

### Post by Therion on 2009-03-13
You can't do updates or software installs in a "Live" environment.  All you can do is pop in the CD, boot to the Live environ and tool-around in Ubuntu "as is".

If you want to upgrade your distro from 7.10 to 8.10 I would strongly *suggest* you backup your data and do a fresh install.

Yes, there ARE other ways to upgrade, but that's what I very strongly suggest you do.  If you just can't bear to go that route just say so though and we can go through another process to do so, fraught with peril as it may be.

---

### Post by satyanash on 2009-03-13
well how do you backup all the softwares that you have on Ubuntu ??? also it never gives you the option of where to install these softwares while installing through the synaptic package manager ?? how can you select where to install the softwares ???

---

### Post by Therion on 2009-03-13
> **sattu94@gmail.com said:**
> well how do you backup all the softwares that you have on Ubuntu ??? also it never gives you the option of where to install these softwares while installing through the synaptic package manager ?? how can you select where to install the softwares ???
Well you really don't want to backup your software, that's one of the main reasons you're upgrading.  You can backup your /config files and such but what I was referring to was backing up your DATA.  If all of that is on a separate partition you may need need to worry about that.

You can't really tell Ubuntu where to install applications as far as I know.  I'm not sure why you'd want to.

Maybe you'd be happier doing a dist-upgrade.  See instructions for how to do this at the site below.  You won't be able to upgrade from 7.10 to 8.10 though, you'll have to upgrade from 7.10 to 8.04 and then upgrade again from 8.04 to 8.10 if you want.  Again, it's not MY suggested method but you can do it this way and it should (should!) preserve your configuration and data.  Don't blame me if it doesn't though, or if it results in an unstable system.

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by satyanash on 2009-03-13
thanks for the site this was really wat i was lookin for

---

