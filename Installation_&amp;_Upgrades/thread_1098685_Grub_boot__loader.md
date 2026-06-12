---
title: "Grub boot  loader"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by rmaries on 2009-03-17
Hi

I installed ubuntu 8.1 from the windows. Now in grub boot loader windows xp option is not there. I cant boot with windows. How can i resolve this?

Thanks
Maries

---

### Post by Denmarx on 2009-03-17
Maries, if you go into the System menu, then Administration, and open the StartUp-Manager, what options do you have in your "Default operating system" menu on the "Boot options" tab? (You'll have to enter your password when you open the StartUp-Manager.)

---

### Post by Mark Phelps on 2009-03-17
> **rmaries said:**
> Hi

I installed ubuntu 8.1 from the windows. Now in grub boot loader windows xp option is not there. I cant boot with windows. How can i resolve this?

Thanks
Maries

You sure you didn't choose the "full disk" option and wipe out XP?

If you open a terminal window and enter "fdisk -lu" (that's a lower-case L, not a one), and it doesn't show FAT32 or NTFS partitions, you wiped out your MS Windows installation.

---

### Post by rmaries on 2009-03-18
Sorry I cant find startup manager in the system->administration menu

---

### Post by Denmarx on 2009-03-21
Hmm. Well, I figure since you're trying to get GRUB set up to let you boot to Windows, you might as well add StartUp-Manager.

Under the Applications menu, choose Add/Remove... and then in the top right search field type StartUp. You'll have a couple options, but just make sure that StartUp-Manager is checked, and then click on "Apply Changes" down in the bottom right.

After it installs, check out what it says.

The "sudo fdisk -l" command on a command line will tell you whether you still have a NTFS or FAT32 partition at all.

---

