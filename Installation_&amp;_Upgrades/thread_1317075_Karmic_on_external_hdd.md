---
title: "Karmic on external hdd"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by msktje on 2009-11-06
Hello,

I've tried to install karmic on my external hdd. Ubiquity crashes on the end when installing grub. I've marked on the last tab in advanced to install grub on dev/sdb. 
I've also tried to recover grub via chroot but that don't work. Now i get the error about not finding the right uid device or something like that. 
Is anyone able to install karmic on an external hdd? And how did you do it when it worked?

---

### Post by msktje on 2009-11-07
As it was a new external hdd i did a proof of concept with a jaunty beta cd that i still had. There it works with no problem. 

In karmic ubiquity and also device-kit-disks crashes on the end of the installation.

---

### Post by msktje on 2009-11-09
Update: I managed to get karmic install to my external hdd. 
I installed the lucid package of devicekit-disks and it's dependency libdbus-glib-1-2. Then the installer can complete succesfully.
Now i can boot the system but i bootproces keeps corrupting the filesystem.
I had one succesfull boot to the graphical envirement. Otherwise the keyboard and mouse freezed at gdm. I think this is a kernel bug.

---

### Post by msktje on 2009-12-30
Is there anyone who could help me with this problem? On boot i get a lot of ext4-fs errors. I have it on karmic and lucid (301209). Or is there someone who has the same problem?

---

